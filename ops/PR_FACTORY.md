# OpenClaw PR Factory（持续运行方案）

## 目标
在可恢复、可审计、可并行的前提下，持续产出高质量小 PR。

## 运行节奏
- 并行任务数：2-3
- 单 PR 范围：只解决 1 个问题
- 优先级：bug/regression > tests > docs mismatch

## 标准流水线（每个任务）
1. 同步上游（fetch upstream + rebase main）
2. 选题（可复现、低耦合、改动小）
3. 新建分支 `fix/<scope>-<issue>`
4. 复现并补测试（优先回归测试）
5. 修复并本地验证
6. push 到 fork
7. 自动创建/更新 PR（关联 issue）
8. 监听 review 并二次提交

## 队列状态定义
- `todo`: 待处理
- `doing`: 处理中
- `pr-open`: 已开 PR
- `blocked`: 阻塞（权限/冲突/CI）
- `done`: 已合并

## 故障策略
- API 失败：指数退避重试（最多 3 次）
- rebase 冲突：转为 blocked，换下一个任务
- CI 失败：优先修复测试，再次推送
- token 失效：立即停止外部写操作并提示轮换 token

## Fork 快速同步策略
通常不重 fork，优先：
- `git fetch upstream`
- `git checkout main && git rebase upstream/main`
- `git push origin main --force-with-lease`（仅在确认无本地独有提交时）

只有在历史严重分叉且持续冲突时才建议重 fork。

## 日志约定
- `daily/YYYY-MM-DD.md`: 当日执行记录
- `prs/open.md`: 活跃 PR 状态
- `retros/weekly.md`: 每周复盘
