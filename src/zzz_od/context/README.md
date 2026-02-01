# 上下文模块 (Context)

## 模块概述
上下文模块负责管理游戏运行时的全局状态和数据，包括：
- 游戏配置和状态
- 空洞模式特定逻辑
- 各种服务实例管理

## 核心类说明

### ZContext
主上下文类，继承自OneDragonContext，包含：
- 游戏配置管理
- 控制器实例
- 各种服务实例
- 运行记录管理

主要功能：
```python
# 初始化上下文
ctx = ZContext()
ctx.init_by_config()

# 获取配置
game_config = ctx.game_config
yolo_config = ctx.yolo_config

# 获取服务实例
map_service = ctx.map_service
compendium_service = ctx.compendium_service
```

### HollowContext
空洞模式上下文，包含：
- 空洞地图识别和处理
- 路径规划
- 角色管理
- 空洞事件处理

主要功能：
```python
# 初始化空洞上下文
ctx.hollow.init_event_yolo(use_gpu=True)

# 识别当前地图
current_map = ctx.hollow.check_current_map(screen, time.time())

# 获取下一步移动路径
next_route = ctx.hollow.get_next_to_move(current_map)
```

## 主要功能

1. **全局状态管理**：
   - 管理游戏配置、控制器和各种服务
   - 提供统一的访问接口

2. **空洞模式支持**：
   - 地图识别和解析
   - 智能路径规划
   - 角色状态跟踪

3. **多线程支持**：
   - 线程安全的上下文访问
   - 异步任务管理

## 使用示例

```python
from zzz_od.context.zzz_context import ZContext

# 初始化上下文
ctx = ZContext()
ctx.init_by_config()

# 空洞模式使用示例
ctx.hollow.init_event_yolo(use_gpu=True)
screen = ctx.controller.screenshot()
current_map = ctx.hollow.check_current_map(screen, time.time())

if current_map:
    next_route = ctx.hollow.get_next_to_move(current_map)
    if next_route:
        # 执行移动操作
        ctx.controller.click(next_route.next_node_to_move.pos.center)
```

## 扩展说明
该模块是游戏自动化运行的核心，所有主要功能都通过上下文对象访问和管理。
