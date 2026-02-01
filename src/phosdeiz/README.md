# Phosdeiz 模块

## 模块概述
Phosdeiz 是一个Python GUI框架和工具集合，提供：
- 文件操作工具
- GUI组件库
- 窗口管理系统
- 样式管理
- 服务层抽象

## 目录结构
- `utils/`: 工具函数
  - `file_utils.py`: 文件路径操作、日期处理等
- `gui/`: GUI框架
  - `widgets/`: 可复用UI组件
  - `windows/`: 窗口管理
  - `qss/`: 样式表
  - `services/`: 服务层

## 核心功能

### 文件工具 (file_utils.py)
- 路径拼接与目录创建
- 项目根目录获取
- 环境变量读取
- 日期时间处理
- 调试文件清理

### GUI框架
1. **组件系统**:
   - 提供基础UI组件
   - 支持自定义样式
2. **窗口管理**:
   - 窗口生命周期管理
   - 多窗口协调
3. **样式系统**:
   - QSS样式表支持
   - 主题切换能力
4. **服务层**:
   - 业务逻辑抽象
   - 数据访问封装

## 使用示例
```python
from phosdeiz.utils.file_utils import get_project_root

# 获取项目根目录
root = get_project_root()
print(f"项目根目录: {root}")
```

## 开发规范
1. 工具函数应保持无状态
2. GUI组件需支持样式定制
3. 服务层应提供清晰接口
4. 遵循PEP8编码规范
