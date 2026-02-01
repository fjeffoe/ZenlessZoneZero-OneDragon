# 项目文件内容总结

## 根目录
### 配置文件
- **.gitignore**
  - 用途: Git版本控制忽略规则文件
  - 内容分类:
    - 开发临时文件（build/, dist/, .idea/等）
    - 用户配置文件（env.bat, config/下的各种yml文件）
    - 执行文件（*.exe）
    - 运行时文件（.log/, .env/等）
    - 模型文件（models/）

- **LICENSE**
  - 用途: 项目许可证文件
  - 许可证类型: GNU通用公共许可证第3版(GPL v3)
  - 主要内容:
    - 允许自由使用、修改和分发软件
    - 要求衍生作品保持相同许可证
    - 提供源代码获取要求
    - 包含免责声明和有限责任条款
    - 详细的使用条款和条件

### 文档文件
- **PROJECT_STRUCTURE.md**
  - 用途: 项目结构说明文档
  - 主要内容:
    - 核心目录结构说明
    - 关键文件功能描述
    - 系统架构图(mermaid格式)
    - 服务模块功能表
    - 配置系统流程图
    - 文件类型统计

- **GUI_STRUCTURE.md**
  - 用途: 图形界面结构说明文档
  - 主要内容:
    - 核心框架文件(app.py, windows.py)
    - 功能界面映射表(7个主要界面)
    - 特殊组件(点赞、代码同步等)
    - 样式服务(PhosStyleSheet)
    - 其他支持文件

### 依赖文件
- **requirements-dev.txt**
  - 用途: 开发环境依赖包列表
  - 主要依赖:
    - GUI框架: pyside6, PySide6-Fluent-Widgets
    - 图像处理: opencv-python, mss
    - 输入控制: pyautogui, pynput
    - 机器学习: onnxruntime-directml
    - 音频处理: soundcard, librosa
    - 数据处理: pyyaml, shapely, pyclipper
    - NLP处理: gensim

## src/zzz_od/yolo/
### 模型文件
- **hollow_event_detector.py**
  - 用途: 空洞事件检测器实现
  - 类结构:
    - 继承自Yolov8Detector
    - 使用ONNX-YOLOv8目标检测模型
  - 主要功能:
    - 检测崩坏星穹铁道游戏中的特殊事件
  - 关键参数:
    - model_name: 模型名称(yolov8n-640-hollow-event)
    - model_parent_dir_path: 模型存储目录
    - gpu: 是否启用GPU加速
    - keep_result_seconds: 结果缓存时间

- **flash_classifier.py**
  - 用途: 闪避分类器实现
  - 类结构:
    - 继承自Yolov8Classifier
    - 使用ONNX-YOLOv8分类模型
  - 主要功能:
    - 识别游戏中的闪避时机
  - 关键参数:
    - model_name: 模型名称(yolov8n-640-dodge-0718)
    - model_parent_dir_path: 模型存储目录
    - gpu: 是否启用GPU加速
    - keep_result_seconds: 结果缓存时间
