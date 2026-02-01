# Windows可执行文件启动器

## 文件列表
- `full_launcher.py`: 完整功能启动器
- `scheduler_launcher.py`: 调度任务启动器

## 功能说明

### full_launcher.py
- **功能**: 启动完整GUI应用程序
- **启动参数**:
  - 主程序: `zzz_od/gui/app.py`
  - `no_windows=True`: 无控制台窗口模式
- **使用场景**:
  - 用户交互式操作
  - 需要完整GUI功能时使用

### scheduler_launcher.py
- **功能**: 启动后台调度任务
- **启动参数**:
  - 主程序: `zzz_od/application/zzz_one_dragon_app.py`
  - `no_windows=False`: 显示控制台窗口
- **使用场景**:
  - 后台定时任务执行
  - 不需要用户交互的场景

## 启动方式
```bash
# 完整功能启动
python full_launcher.py

# 调度任务启动 
python scheduler_launcher.py
