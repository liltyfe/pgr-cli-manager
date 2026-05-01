# PGR CLI Manager

战双帕弥什命令行管理器。当前项目基于 [ww-manager](https://github.com/timetetng/wutheringwaves-cli-manager)
改造，目标是为《战双帕弥什》PC 客户端提供基础的下载、校验和修复能力。感谢大佬开源

做这个项目的初衷很简单，我在使用 `Arch Linux`
玩战双的时候，发现官方的下载器没有办法渲染，导致资源没有办法下载，在搜索解决方案的时候，无意之间发现了
`ww-manager` 这个项目，于是仿照鸣潮的cli启动器写了一个站双的。

> 当前处于早期开发阶段，只适配国服 `cn`。B 服、国际服、快速切服、预下载和抽卡链接分析暂未实现。

## 功能

- 下载战双帕弥什国服客户端。
- 根据官方资源清单校验本地文件。
- 自动下载缺失或大小/MD5 不匹配的文件。
- 记住默认游戏目录，后续命令可省略 `--path`。

## 安装与开发

本项目使用 `uv` 管理 Python 环境。

```bash
uv sync
```

查看命令帮助：

```bash
uv run pgr --help
```

本地构建：

```bash
uv build
```

## 使用

首次使用时指定游戏安装目录：

```bash
pgr -p "$HOME/Games/PGR" status
```

下载国服客户端：

```bash
pgr -p "$HOME/Games/PGR" download cn
```

之后路径会被保存，可以直接运行：

```bash
pgr status
pgr sync
```

## 命令

### `status`

查看当前目录的本地配置、服务器和版本。

```bash
pgr status
```

### `download`

下载完整客户端。

```bash
pgr download cn
```

### `sync`

全量校验并修复文件。该命令会计算 MD5，适合修复损坏或缺失的文件。

```bash
pgr sync
```

## 当前限制

- 只支持国服 `cn`。
- 未实现服务器切换。
- 未实现预下载资源应用。
- 未实现抽卡记录链接提取。
- 资源入口 URL 目前写在 `src/pgr_manager/config.py`，如果官方启动器配置路径变化，需要更新该文件。

## 致谢

本项目基于 `ww-manager` 的实现思路改造，复用了其 CLI、资源清单解析、文件校验和并发下载结构。
