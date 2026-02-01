# 游戏操作模块

## 核心文件
- `zzz_operation.py`: 操作基类
- `back_to_normal_world.py`: 返回大世界操作
- `choose_predefined_team.py`: 选择预设队伍
- `deploy.py`: 部署操作
- `eat_noodle.py`: 进食操作
- `key_sim_runner.py`: 按键模拟
- `open_menu.py`: 打开菜单
- `transport.py`: 传送操作
- `wait_normal_world.py`: 等待大世界状态

## 子目录
- `arcade/`: 街机相关操作
- `challenge_mission/`: 挑战任务
- `compendium/`: 快捷手册操作
- `enter_game/`: 进入游戏
- `hdd/`: 硬盘相关操作

## 操作基类 (ZOperation)
- **功能**:
  - 提供操作执行框架
  - 处理重试逻辑
  - 管理操作回调
- **关键参数**:
  - `node_max_retry_times`: 节点最大重试次数
  - `timeout_seconds`: 超时时间
  - `need_check_game_win`: 是否需要检查游戏窗口

## 典型操作流程
1. 初始化操作上下文
2. 执行操作节点(operation_node)
3. 处理操作结果
4. 根据结果决定重试或继续

## 示例操作: BackToNormalWorld
- **功能**: 确保角色返回大世界
- **实现**:
  - 检查当前画面状态
  - 处理各种特殊情况(战斗、空洞、对话等)
  - 执行返回操作
- **技术**:
  - 使用OCR识别界面元素
  - 基于CV2的图像处理
