# 说明

复制自 https://github.com/jingsongliujing/OnnxOCR

更新时间 2024.08.08

改动说明

- 将模型、字体、文本放入 assets/models/onnx_ocr 中

# ONNX OCR 模块

## 模块概述
基于ONNX Runtime实现的OCR识别系统，提供：
- 文字检测
- 方向分类
- 文字识别
- 结果后处理

## 核心文件
- `predict_system.py`: 主系统入口
- `predict_det.py`: 文字检测
- `predict_cls.py`: 方向分类
- `predict_rec.py`: 文字识别
- `utils.py`: 工具函数

## 处理流程
1. **文字检测**:
   - 定位图像中的文字区域
   - 输出检测框坐标

2. **方向分类** (可选):
   - 判断文字方向
   - 自动旋转校正

3. **文字识别**:
   - 识别检测框内的文字内容
   - 输出识别结果和置信度

4. **后处理**:
   - 过滤低置信度结果
   - 对检测框排序(从上到下，从左到右)

## 核心类说明

### TextSystem
- **功能**: OCR系统主类
- **主要方法**:
  - `__call__`: 执行完整OCR流程
  - `draw_crop_rec_res`: 保存裁剪的识别区域

### 使用示例
```python
from onnxocr.predict_system import TextSystem

# 初始化OCR系统
args = {...}  # 配置参数
text_sys = TextSystem(args)

# 执行OCR识别
img = cv2.imread('test.jpg')
boxes, rec_res = text_sys(img)

# 输出结果
for box, (text, score) in zip(boxes, rec_res):
    print(f"文本: {text}, 置信度: {score:.2f}, 位置: {box}")
```

## 性能优化
1. 使用ONNX Runtime加速推理
2. 支持批量处理
3. 可配置的置信度阈值
4. 多种检测框类型支持(四边形/最小外接矩形)
