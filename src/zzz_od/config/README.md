# 配置模块 (Config)

## 模块概述
配置模块负责管理游戏运行时的各种配置参数，包括：
- 游戏基础设置
- 队伍配置
- YOLO模型配置

## 配置文件说明

### game_config.py
游戏基础配置，包含：
- 游戏平台、语言、区服设置
- 游戏路径、账号信息
- 键盘/手柄按键映射
- 输入方式设置

主要配置项：
```python
platform = "PC"  # 游戏平台
game_language = "cn"  # 游戏语言
game_region = "cn"  # 游戏区服
game_path = ""  # 游戏安装路径
key_normal_attack = "mouse_left"  # 普通攻击按键
key_dodge = "shift"  # 闪避按键
```

### team_config.py
队伍配置管理，包含：
- 预设队伍列表
- 队伍自动战斗配置
- 队伍管理接口

主要功能：
```python
# 获取队伍列表
team_list = team_config.team_list

# 更新队伍配置
team_config.update_team(team_info)
```

### yolo_config.py
YOLO模型配置，包含：
- 闪光分类器模型设置
- 空洞事件检测模型设置
- GPU加速配置

主要配置项：
```python
flash_classifier = "yolov8n-640-flash-0718"  # 闪光分类器模型
hollow_zero_event = "yolov8s-736-hollow-zero-event-1027"  # 空洞事件模型
flash_classifier_gpu = True  # 是否使用GPU加速
```

## 使用示例

```python
from zzz_od.config.game_config import GameConfig
from zzz_od.config.team_config import TeamConfig
from zzz_od.config.yolo_config import YoloConfig

# 初始化配置
game_config = GameConfig(0)
team_config = TeamConfig(0) 
yolo_config = YoloConfig()

# 读取配置
print(game_config.game_language)
print(team_config.team_list[0].name)
print(yolo_config.flash_classifier)

# 更新配置
game_config.game_language = "en"
team_config.update_team(new_team_info)
yolo_config.flash_classifier_gpu = False
```

## 配置文件位置
所有配置文件存储在`config/`目录下，以YAML格式保存。
