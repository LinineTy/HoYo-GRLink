# HoYo GRLink

> 米哈游抽卡链接提取工具，当前已支持《崩坏：星穹铁道》《原神》《绝区零》的抽卡记录 URL 提取。

## 功能

- 自动检测游戏缓存目录，获取最新抽卡链接
- 支持星穹铁道 / 原神 / 绝区零
- 历史操作记录存档
- 适配浅色 / 深色模式，支持自适应调节
- 纯本地运行，不联网上传任何数据

## 使用方法

1. 打开游戏，进入抽卡记录页面
2. 运行 `HoYo GRLink`，选择对应的游戏和服务器（国服 / 国际服）
3. 点击获取链接，自动复制到剪贴板
4. 粘贴到任意抽卡分析工具使用（如"小黑盒"）

## 下载

从 [Releases 页](https://github.com/LinineTy/HoYo-GRLink/releases) 下载最新的 HoYo_GRLink.exe，双击即可运行。

## 构建

### 前置依赖

- [Go](https://go.dev/dl/) ≥ 1.21
- [Node.js](https://nodejs.org/) ≥ 18
- [LLVM MinGW](https://github.com/mstorsjo/llvm-mingw)（C 编译器，用于 Wails CGO）
- Python 3 + Pillow（图标生成脚本）

### 构建步骤

```bash
# 双击 build.bat，或手动执行：
python scripts/regenerate_ico.py
go run scripts/gen_build_time.go
wails build -ldflags "$(go run scripts/gen_build_time.go)"
```

## 技术栈

| 层 | 技术 |
|---|---|
| 后端 | Go + [Wails v2](https://wails.io/) |
| 前端 | [Svelte 5](https://svelte.dev/) (runes mode) |
| 设计 | Material Design 3 纯手写 CSS |
| 图标 | SVG path 内联 |
| 字体 | MiSans Normal |

## 致谢

部分链接解析逻辑基于2023年旧版小黑盒社区提供方案，在此表示感谢。
