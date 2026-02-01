# yolo 目录说明

## 文件列表
- `hollow_event_detector.py`: 空洞事件检测器实现
- `flash_classifier.py`: 闪避分类器实现

## hollow_event_detector.py
### 功能
- 检测崩坏星穹铁道游戏中的特殊事件
- 基于YOLOv8的目标检测模型

### 类结构
- 继承自 `Yolov8Detector`
- 使用ONNX-YOLOv8模型

### 关键参数
| 参数 | 类型 | 说明 |
|------|------|------|
| model_name | str | 模型名称(yolov8n-640-hollow-event) |
| gpu | bool | 是否启用GPU加速 |
| keep_result_seconds | float | 结果缓存时间(秒) |

## flash_classifier.py  
### 功能
- 识别游戏中的闪避时机
- 基于YOLOv8的分类模型

### 类结构
- 继承自 `Yolov8Classifier`
- 使用ONNX-YOLOv8模型

### 关键参数
| 参数 | 类型 | 说明 |
|------|------|------|
| model_name | str | 模型名称(yolov8n-640-dodge-0718) | 
| gpu | bool | 是否启用GPU加速 |
| keep_result_seconds | float | 结果缓存时间(秒) |

## 依赖关系
- 需要安装onnxruntime-directml包
- 依赖父目录的yolo_utils模块
