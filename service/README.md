# 服务模块说明

## 文件列表
- `zzz_base_scheduler.py`: 基础调度服务
- `zzz_syn_battle_service.py`: 战斗数据同步服务
- `zzz_shared_battle_service.py`: 战斗数据API服务
- `zzz_data_model.py`: 数据模型定义
- `zzz_save_battle_class.py`: 战斗数据存储类

## 核心服务功能

### 1. zzz_base_scheduler.py
- **功能**: 异步任务调度器
- **主要组件**:
  - AsyncIOScheduler: 异步IO调度器
  - SynBattle: 战斗数据同步服务
- **调度任务**:
  - 每60秒执行一次数据同步

### 2. zzz_syn_battle_service.py
- **功能**: 从群文件同步战斗配置
- **核心类**:
  - `SynBattle`: 处理战斗数据同步
- **主要方法**:
  - `fetch_data()`: 获取群文件列表并检查更新
  - `getFileUrl()`: 获取文件下载URL并保存

### 3. zzz_shared_battle_service.py
- **功能**: 提供战斗数据API服务
- **API端点**:
  - `GET /getBattleInfo`: 查询所有战斗数据
  - `POST /uploadBattleInfo`: 上传战斗配置
  - `GET /downloadBattleInfo/{bid}`: 下载指定战斗配置
- **技术栈**:
  - FastAPI框架
  - Uvicorn服务器

## 服务关系图
```mermaid
graph TD
    A[zzz_base_scheduler.py] -->|调度| B[zzz_syn_battle_service.py]
    B -->|保存数据| C[zzz_data_model.py]
    D[zzz_shared_battle_service.py] -->|查询数据| C
    C -->|数据存储| E[zzz_save_battle_class.py]
