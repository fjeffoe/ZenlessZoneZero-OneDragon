# 动作记录模块 (Action Recorder)

## 模块概述
动作记录模块用于录制游戏战斗中的操作序列，并自动生成可复用的战斗动作模板。主要功能包括：
- 实时记录键盘鼠标操作
- 同步捕获游戏战斗状态
- 智能分析操作模式
- 自动生成YAML格式的配置模板

## 核心文件
- `monitor.py`: 动作和状态记录核心
- `template_generator.py`: 模板生成器

## 主要功能

### 1. 动作状态记录
- 实时捕获键盘和鼠标操作
- 同步记录游戏战斗状态：
  - 角色站位和状态
  - 技能可用状态
  - 闪避触发状态
  - 连携技状态

### 2. 智能模板生成
- 基于机器学习聚类分析操作模式
- 自动识别常用连招组合
- 生成最优操作序列模板
- 支持特殊状态处理：
  - 闪避反应
  - 连携技选择
  - 终结技释放
  - 快速支援切换

### 3. 模板优化
- 自动去重和合并相似操作
- 识别长按/短按操作差异
- 适配不同角色的操作习惯
- 支持与现有模板融合

## 使用示例

```python
from zzz_od.action_recorder.monitor import RecordContext
from zzz_od.context.zzz_context import ZContext

# 初始化上下文
ctx = ZContext()
ctx.init_by_config()

# 开始录制
recorder = RecordContext(ctx)
recorder.records_status_and_action()  # 进入录制状态
recorder.output_records()  # 输出录制结果

# 生成模板
from zzz_od.action_recorder.template_generator import PreProcessor, SelfAdaptiveGenerator
pp = PreProcessor()
merged_status_ops = pp.pre_process()

sag = SelfAdaptiveGenerator(merged_status_ops, pp.agent_names)
agent_templates, special_status = sag.get_templates()
sag.output_yaml(agent_templates, special_status)  # 生成YAML模板
```

## 输出格式
模块最终会生成标准化的YAML配置文件，包含：
- 角色站场模板
- 闪避反应配置
- 连携技处理逻辑
- 特殊状态处理
- 操作间隔设置

生成的模板可直接用于自动战斗系统配置。
