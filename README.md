# Desktop Clock 桌面时钟

一个功能丰富的桌面时钟应用，支持双时区显示、农历日历、天气信息和插件系统。

## 功能特性

| 模块 | 说明 |
| --- | --- |
| 双时区显示 | 选择不同时区进行对比，显示当前时间、日期与农历节气 |
| 模拟钟表 | 实时显示主时间，带钟表表盘 |
| 天气信息 | 按城市自动获取天气，显示天气图标与温度 |
| 界面功能 | 窗口透明度可调、精简/完整模式切换、窗口拖动、置顶显示 |
| 插件系统 | 动态加载第三方插件，提供插件管理界面，支持时间与天气事件通知 |

## 运行要求

- Python 3.x
- 依赖库：`requests`、`lunar_python`（已列在 `requirements.txt`）

## 安装与运行

```bash
pip install -r requirements.txt
python desktop_clock.py
```

若使用虚拟环境：

```bash
venv\Scripts\pip install -r requirements.txt
venv\Scripts\python.exe desktop_clock.py
```

## 使用说明

1. **拖动窗口** —— 点击并拖动标题栏即可移动窗口位置
2. **切换时区** —— 在下拉菜单中选择想要显示的时区
3. **切换模式** —— 点击「精简模式」/「完整模式」按钮切换显示模式
4. **调节透明度** —— 拖动底部滑块调整窗口透明度
5. **插件管理** —— 点击「插件」按钮查看已加载的插件
6. **关闭窗口** —— 点击右上角的关闭按钮

## 插件系统

### 目录结构

```
plugins/
├── plugin_base.py        # 插件基类
├── plugin_manager.py     # 插件管理器
└── example_plugins/      # 示例插件目录
```

### 创建自定义插件

1. 在 `plugins/example_plugins/` 目录下创建新的 `.py` 文件
2. 继承 `Plugin` 基类
3. 实现需要的方法（`initialize`、`on_time_update`、`on_weather_update` 等）

```python
from plugins.plugin_base import Plugin

class MyPlugin(Plugin):
    def __init__(self):
        self.name = "My Plugin"
        self.version = "1.0.0"
        self.description = "我的自定义插件"

    def on_time_update(self, current_time):
        # 时间更新时触发
        pass

    def on_weather_update(self, weather_data):
        # 天气更新时触发
        pass
```

## 文件结构

```
├── desktop_clock.py            # 主程序
├── requirements.txt            # 依赖清单
├── plugins/                    # 插件目录
│   ├── plugin_base.py          # 插件基类
│   ├── plugin_manager.py       # 插件管理器
│   └── example_plugins/        # 示例插件
│       ├── world_clock_plugin.py
│       └── weather_plugin.py
└── README.md
```

## 技术栈

- Python 3.x
- Tkinter —— GUI 框架
- requests —— 天气 API 请求
- lunar_python —— 农历计算
- zoneinfo —— 时区处理

## 天气数据源

天气信息来自 [wttr.in](https://wttr.in) 免费天气 API 服务。

## 注意事项

1. 需要网络连接才能获取天气信息
2. 默认显示亚洲/上海时区与 UTC 时区
3. 程序启动后会自动置顶显示
4. 插件会在程序启动时自动加载

## 版本

- v1.1.0 —— 添加插件系统

## 作者

hellojint
