# simlp

一个用于承载 **ComfyUI** 的 git submodule 的仓库。

| 项 | 内容 |
| - | - |
| 子模块 | `ComfyUI` → <https://github.com/Comfy-Org/ComfyUI>（分支 `master`） |
| 当前 pin | `858fd58dcd47b1407a6778e0920f02a9b40fd538` |
| 用途 | 把 ComfyUI 作为子模块固定版本，便于随本仓库一起克隆与协作 |

## 为什么用 submodule 而不是直接 clone

- **锁版本**：主仓只记录一个 commit SHA，任何人 clone 得到的 ComfyUI 完全一致，避免上游更新导致环境漂移。
- **轻量**：不需要把 ComfyUI 的完整历史拉进本仓库，`git clone --recurse-submodules` 即可拉取指定版本。
- **可增量升级**：需要升级时 `git submodule update --remote ComfyUI` 后提交新的 SHA 即可。

## 使用方法

```bash
# 克隆本仓库并同时拉取子模块
git clone --recurse-submodules https://github.com/simlpandordinary/simlp.git

# 已经克隆过、只想补拉子模块
cd simlp && git submodule update --init --recursive
```

更新到指定版本：

```bash
cd ComfyUI && git fetch && git checkout 858fd58dcd47b1407a6778e0920f02a9b40fd538
```

## 许可

本仓库自身的文件（README、.gitmodules 等）以 MIT 发布，见 [LICENSE](LICENSE)。

**子模块 `ComfyUI` 遵循其上游仓库自身的许可证**（GPL-3.0），不随本仓库的 MIT 授权；使用 ComfyUI 时请遵循其许可条款。
