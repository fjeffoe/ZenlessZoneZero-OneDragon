# ZenlessZoneZero-OneDragon GUI 结构文档

## 核心框架文件

| 文件路径 | 功能描述 |
|---------|----------|
| `src/zzz_od/gui/app.py` | 主窗口实现，管理所有子界面 |
| `src/zzz_od/gui/windows.py` | AppWindowBase基类(提供基础窗口功能) |

## 功能界面映射

| 界面类 | 对应目录 | 功能描述 |
|-------|---------|----------|
| HomeInterface | `src/zzz_od/gui/view/home/` | 主页面展示 |
| BattleAssistantInterface | `src/zzz_od/gui/view/battle_assistant/` | 战斗辅助功能 |
| ZOneDragonInterface | `src/zzz_od/gui/view/one_dragon/` | 一条龙自动化流程 |
| HollowZeroInterface | `src/zzz_od/gui/view/hollow_zero/` | 空洞挑战功能 |
| GameAssistantInterface | `src/zzz_od/gui/view/game_assistant/` | 游戏辅助工具 |
| AppDevtoolsInterface | `src/zzz_od/gui/view/devtools/` | 开发者工具 |
| AppSettingInterface | `src/zzz_od/gui/view/setting/` | 系统设置界面 |

## 特殊组件

| 组件 | 来源文件 | 功能描述 |
|------|---------|----------|
| LikeInterface | `one_dragon.gui.view.like_interface` | 点赞反馈功能 |
| CodeInterface | `one_dragon.gui.view.code_interface` | 代码同步功能 |
| ContextEventSignal | `one_dragon.gui.view.context_event_signal` | 上下文事件信号处理 |

## 样式服务

| 服务 | 来源文件 | 功能描述 |
|------|---------|----------|
| PhosStyleSheet | `phosdeiz.gui.services` | 全局样式管理 |

## 其他支持文件

| 文件/目录 | 功能描述 |
|----------|----------|
| `__init__.py` | 包初始化文件 |
| `installer/` | 安装程序相关界面 |
