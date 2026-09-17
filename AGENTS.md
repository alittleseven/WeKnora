# WeKnora（本地 fork）— 项目级准则

> 本仓库是 `Tencent/WeKnora` 的个人 fork（`alittleseven/WeKnora`），检出于工作区 `projects/WeKnora`。
> 本文件只约束本地 fork 的分支策略，不修改上游代码规范。

## 分支策略（2026-09-18 Human 拍板，永久有效）

| 分支 | 用途 | 规则 |
|------|------|------|
| `main` | **只用于同步上游** | 定期 `merge upstream/main` 跟进 Tencent/WeKnora；仅允许本地收编类 chore 提交；**永不接受 local-custom 的合入** |
| `local-custom` | **自修改分支** | 所有本地定制（配置、补丁、收编文件）只在此分支进行；定期从 `main` 合入上游更新；**永不合入 main** |

## 上游同步流程（main → local-custom 单向流动）

```bash
git fetch upstream                     # upstream = git@github.com:Tencent/WeKnora.git
git switch main && git merge upstream/main   # main 跟进上游
git switch local-custom && git merge main    # 上游更新单向流入自修改分支
```

- 禁止反向操作：`git merge local-custom`（在 main 上）、`git push origin local-custom:main` 均不允许。
- `origin` = git@github.com:alittleseven/WeKnora.git（个人 fork）。

## 其他约定

- 遵守工作区根 `AGENTS.md` 全局准则（分档、点名技能、提交规范）。
- 上游代码不做无关重构；本地定制尽量集中在独立文件/目录，减少与上游合并冲突面。
