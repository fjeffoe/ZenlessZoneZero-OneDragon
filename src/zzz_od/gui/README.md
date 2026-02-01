# GUI 模块说明

## 核心文件
- `app.py`: 主程序入口文件
- `windows.py`: 窗口基类定义
- `view/`: 各功能界面实现

## app.py 主程序

### AppWindow 主窗口类
- **功能**:
  - 应用程序主窗口
  - 管理各功能子界面
  - 处理主题和样式设置
  - 响应上下文事件

### 主要方法
| 方法 | 说明 |
|------|------|
| `__init__` | 初始化窗口标题和图标 |
| `init_window` | 设置窗口大小、位置和样式 |
| `create_sub_interface` | 创建并添加所有子界面 |

### 子界面列表
1. `HomeInterface`: 主页面
2. `BattleAssistantInterface`: 战斗助手
3. `ZOneDragonInterface`: 一条龙流程
4. `HollowZeroInterface`: 空洞挑战
5. `GameAssistantInterface`: 游戏助手
6. `LikeInterface`: 点赞功能
7. `AppDevtoolsInterface`: 开发工具
8. `CodeInterface`: 代码同步
9. `AppSettingInterface`: 系统设置

## 样式系统
- 使用 `PhosStyleSheet` 管理界面样式
- 支持主题切换(light/dark)
- 应用样式到各组件:
  - 主窗口
  - 导航栏
  - 堆叠窗口
  - 标题栏

## 启动流程
1. 初始化QApplication
2. 创建ZContext上下文
3. 加载配置
4. 设置主题
5. 创建并显示主窗口
6. 启动事件循环
