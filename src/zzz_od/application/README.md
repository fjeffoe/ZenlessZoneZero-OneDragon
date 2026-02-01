# 应用模块 (Application)

## 模块概述
应用模块是系统的核心执行单元，负责管理和调度各类游戏自动化任务。主要特点：
- 基于OneDragon框架的应用扩展
- 支持多应用并行调度
- 提供统一的执行入口
- 集成各类游戏功能模块

## 核心类

### ZApplication
应用基类，继承自`one_dragon.base.operation.application_base.Application`，提供：
- 应用基础执行流程
- 游戏窗口管理
- 上下文初始化/清理
- 错误重试机制

### ZOneDragonApp
主应用类，继承自`OneDragonApp`和`ZApplication`，功能包括：
- 集成所有子应用
- 提供统一执行入口
- 支持账号切换
- 任务完成后自动处理(关机/关闭游戏等)

## 子应用列表
| 子应用 | 功能描述 |
|--------|----------|
| RedemptionCodeApp | 兑换码兑换 |
| WeeklyScheduleApp | 周常任务 |
| EmailApp | 邮件领取 |
| RandomPlayApp | 随机玩法 |
| ScratchCardApp | 刮刮乐 |
| ChargePlanApp | 充值计划 |
| CoffeeApp | 咖啡厅 |
| NotoriousHuntApp | 通缉令 |
| EngagementRewardApp | 活跃奖励 |
| HollowZeroApp | 空洞玩法 |
| ShiyuDefenseApp | 时雨防御 |
| CityFundApp | 城市基金 |
| LifeOnLineApp | 在线时长 |

## 使用示例

```python
from zzz_od.context.zzz_context import ZContext
from zzz_od.application.zzz_one_dragon_app import ZOneDragonApp

# 初始化上下文
ctx = ZContext()
ctx.init_by_config()

# 创建并执行应用
app = ZOneDragonApp(ctx)
app.execute()

# 执行特定子应用
from zzz_od.application.hollow_zero.hollow_zero_app import HollowZeroApp
hollow_app = HollowZeroApp(ctx)
hollow_app.execute()
```

## 调试模式
模块提供内置调试入口：
```python
if __name__ == '__main__':
    __debug()  # 直接运行zzz_one_dragon_app.py进入调试模式
```

调试模式支持：
- 自动代码更新
- 任务完成后自动关机/关闭游戏
- 完整的异常处理
