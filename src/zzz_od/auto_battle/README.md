# 自动战斗模块 (Auto Battle)

## 模块概述
自动战斗模块负责游戏战斗场景的自动化操作，包括：
- 战斗状态识别
- 角色技能管理
- 连携技处理
- 闪避反应
- 战斗操作执行

## 核心组件

### AutoBattleContext
战斗上下文，负责：
- 管理战斗状态
- 提供战斗操作接口
- 处理按键状态
- 协调各子模块工作

主要功能：
```python
# 战斗操作接口
dodge()  # 闪避
switch_next()  # 切换下一个角色
normal_attack()  # 普通攻击
special_attack()  # 特殊攻击
ultimate()  # 终结技
chain_left()  # 左连携技
chain_right()  # 右连携技
```

### AutoBattleOperator
战斗操作器，负责：
- 解析战斗配置
- 管理原子操作
- 处理状态互斥
- 执行战斗流程

### BattleStateEnum
战斗状态枚举，定义：
- 所有可用的战斗按键
- 技能可用状态
- 连携技状态

## 状态管理

### 角色状态
- 前台角色状态
- 后台角色状态
- 连携技角色状态
- 快速支援状态

### 技能状态
- 特殊攻击可用
- 终结技可用
- 连携技可用
- 快速支援可用

## 操作流程

1. 初始化战斗上下文
```python
auto_battle_context.init_battle_context(
    auto_op=operator,
    use_gpu=True,
    check_dodge_interval=0.02,
    # 其他参数...
)
```

2. 启动战斗
```python
auto_battle_context.start_context()
```

3. 执行战斗循环
- 识别战斗状态
- 执行对应操作
- 处理特殊状态(闪避/连携技等)

4. 结束战斗
```python
auto_battle_context.stop_context()
```

## 使用示例

```python
from zzz_od.context.zzz_context import ZContext
from zzz_od.auto_battle.auto_battle_operator import AutoBattleOperator

# 初始化上下文
ctx = ZContext()
ctx.init_by_config()

# 创建自动战斗操作器
auto_op = AutoBattleOperator(ctx, 'auto_battle', '测试配置')

# 初始化并启动
auto_op.init_before_running()
auto_op.start_running_async()

# 运行一段时间后停止
import time
time.sleep(60)
auto_op.stop_running()
```

## 配置文件
- `config/auto_battle_operation/`: 操作模板
- `config/auto_battle_state_handler/`: 状态处理器模板
