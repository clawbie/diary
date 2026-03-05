# Open PRs

- openclaw/openclaw#36350 fix(cron): persist payload.fallbacks on update (Closes #36263)
  https://github.com/openclaw/openclaw/pull/36350

- openclaw/openclaw#36298 fix(gateway): create transcript for chat.inject when missing (Closes #36170)
  https://github.com/openclaw/openclaw/pull/36298

- openclaw/openclaw#35885 fix(browser): allow disabling AutomationControlled flag (Closes #35721)
  https://github.com/openclaw/openclaw/pull/35885
  - Update: add unit test + ensure `!--...` negation directive is not forwarded to Chrome.

- openclaw/openclaw#35935 fix(cron): write store and run logs with owner-only perms (Closes #35881)
  https://github.com/openclaw/openclaw/pull/35935

- openclaw/openclaw#35849 fix(config): accept openclaw browser driver in schema (Closes #35620)
  https://github.com/openclaw/openclaw/pull/35849

- #35496 — fix(telegram): make model picker checkmark provider-aware for duplicate model IDs
  - https://github.com/openclaw/openclaw/pull/35496
  - State: OPEN
  - Linked issue: #35476
  - Next action: 等 CI/Reviewer 反馈，收到意见后自动跟进修订。

- #35625 — fix(discord): accept agentComponents in strict config schema
  - https://github.com/openclaw/openclaw/pull/35625
  - State: OPEN
  - Linked issue: #35564
  - Next action: 等 CI/Reviewer 反馈，按评论最小范围修订。

- #35778 — fix(whatsapp): clarify allowFrom denial error
  - https://github.com/openclaw/openclaw/pull/35778
  - State: OPEN
  - Linked issue: #35580
  - Next action: 等 CI/Reviewer 反馈；如 maintainer 希望更短文案或变更 error type，再按建议微调。

- #35800 — fix(bluebubbles): avoid debounce crash on null text
  - https://github.com/openclaw/openclaw/pull/35800
  - State: OPEN
  - Linked issue: #35777
  - Next action: 等 CI/Reviewer 反馈；若 maintainer 希望更严格的类型保障（normalize 阶段修正 text 字段），按建议微调。

- #35815 — fix(system-prompt): include channel messageToolHints in minimal mode
  - https://github.com/openclaw/openclaw/pull/35815
  - State: OPEN
  - Linked issue: #35795
  - Next action: 等 CI/Reviewer 反馈；如 maintainer 更倾向在 subagent direct-send 路径做格式转换，再按建议调整实现位置。

- #35849 — fix(config): accept openclaw browser driver in schema
  - https://github.com/openclaw/openclaw/pull/35849
  - State: OPEN
  - Linked issue: #35620
  - Next action: 等 CI/Reviewer 反馈；如 maintainer 希望仅支持 `openclaw` 并移除 legacy `clawd`，按建议调整兼容策略。

- #36370 — fix(telegram): render markdown tables as code by default
  - https://github.com/openclaw/openclaw/pull/36370
  - State: OPEN
  - Linked issue: #36323
  - Next action: 等 CI/Reviewer 反馈；若 maintainer 更希望默认 bullets 模式（更易读），可按建议调整默认/文档。

- #36403 — fix(models): preserve kimi-coding baseUrl from explicit config
  - https://github.com/openclaw/openclaw/pull/36403
  - State: OPEN
  - Linked issue: #36353
  - Next action: 等 CI/Reviewer 反馈；如 maintainer 希望只在显式配置存在时才启用 implicit provider，或想复用 mergeWithExistingProviderSecrets 策略，再按建议微调。

- #36426 — fix(skill-creator): reject empty SKILL.md name/description
  - https://github.com/openclaw/openclaw/pull/36426
  - State: OPEN
  - Linked issue: #36385
  - Next action: 等 CI/Reviewer 反馈；如 maintainer 想把 error message 合并为统一的 “missing/empty” 文案，再按建议调整。
