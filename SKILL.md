---
name: simlp
description: ComfyUI 的 git submodule 容器仓库，锁定 ComfyUI 版本（当前 pin 858fd58）。当需要克隆/升级 ComfyUI、保持多机版本一致、或为 ComfyUI 项目选基线版本时使用本技能。
---

# ComfyUI 子模块容器仓（simlp）

> 本技能是 GitHub 仓库 [`simlpandordinary/simlp`](https://github.com/simlpandordinary/simlp) 的**安装入口与使用索引**。
> 该仓库是代码/资源仓库（本身没有 Agent Skill 定义），因此这里写清楚「它是什么、能干什么、怎么取到代码、注意事项」，
> 让 AI 在相关任务中能直接定位并正确使用它。

## 仓库档案

| 项 | 内容 |
| - | - |
| 仓库 | <https://github.com/simlpandordinary/simlp> |
| 默认分支 | `main` |
| 体积 | 1 KB |
| 许可 | MIT |
| 来源 | ComfyUI 的 git submodule 容器仓库：锁定版本、轻量克隆、可增量升级 |
| 顶层内容 | .gitmodules / LICENSE / NOTICE.md / README.md |

## 能干什么

本仓库本身不含 ComfyUI 源码，只以 **git submodule** 的形式引用 <https://github.com/Comfy-Org/ComfyUI>，好处是：

- **锁版本**：主仓只记录一个 commit SHA，任何人克隆得到的 ComfyUI 完全一致，不会因上游更新导致环境漂移；
- **轻量**：不需要把 ComfyUI 的完整历史拉进本仓库；
- **可增量升级**：`git submodule update --remote ComfyUI` 后提交新的 SHA 即可。

```bash
git clone --recurse-submodules https://github.com/simlpandordinary/simlp.git
# 已克隆过、只补拉子模块
cd simlp && git submodule update --init --recursive
```

## 怎么把代码取到本机

本机到 `github.com` 主站的直连与代理都不稳定，按优先级：

```bash
# 1) 镜像 clone（在本机验证可用，最快）
git clone https://ghfast.top/https://github.com/simlpandordinary/simlp.git

# 2) 只想读某几个文件 → 走 API（api.github.com 直连可用）
curl -s https://api.github.com/repos/simlpandordinary/simlp/contents/<path>

# 3) 需要完整历史 → 用 GitHub 服务端 fork/镜像
```

克隆后请先读该仓库的 `README.md` 与 `INSTALL.md`，再按其官方步骤装依赖。

## 许可

本仓库自有文件（README、.gitmodules、LICENSE）以 MIT 发布；**子模块 ComfyUI 遵循其上游的 GPL-3.0**，不在 MIT 授权范围内。
