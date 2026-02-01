# 零号空洞挑战模块

## 核心文件
- `hollow_runner.py`: 主运行逻辑
- `hollow_battle.py`: 空洞战斗处理
- `hollow_exit_by_menu.py`: 通过菜单退出空洞
- `hollow_level_info.py`: 层级信息管理
- `hollow_zero_challenge_config.py`: 挑战配置
- `hollow_zero_data_service.py`: 数据服务

## 子目录
- `event/`: 各类事件处理器
- `game_data/`: 游戏数据定义
- `hollow_map/`: 空洞地图和寻路

## 核心功能

### HollowRunner 主运行类
- **功能**:
  - 管理空洞挑战全流程
  - 处理各类特殊事件
  - 控制自动寻路
  - 处理战斗和奖励

### 主要方法
| 方法 | 说明 |
|------|------|
| `check_screen` | 识别当前画面状态 |
| `_handle_event` | 处理识别到的事件 |
| `_handle_map_move` | 处理地图移动逻辑 |
| `exit_hollow` | 退出空洞流程 |

## 事件处理系统
- **特殊事件处理器**:
  - 邦布商人(BambooMerchant)
  - 支援请求(CallForSupport)
  - 关键进展(CriticalStage)
  - 门扉战斗(DoorBattle)
  - 以太确认(ConfirmResonium)
  - 以太升级(UpgradeResonium)

- **事件处理流程**:
  1. 识别画面事件类型
  2. 匹配对应事件处理器
  3. 执行事件处理逻辑
  4. 更新处理状态

## 自动寻路系统
- **组件**:
  - `HollowZeroMap`: 空洞地图数据
  - `RouteSearchRoute`: 寻路算法
  - `HollowZeroMapNode`: 地图节点

- **寻路流程**:
  1. 识别当前地图状态
  2. 计算最优路径
  3. 点击目标格子
  4. 处理移动后事件

## 配置系统
- **hollow_zero_challenge_config.py**:
  - 额外任务配置
  - 退出条件设置
  - 挑战参数调整
