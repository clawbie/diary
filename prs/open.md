# Open PRs

- openclaw/openclaw#36313 fix(gateway): create transcript for chat.inject when missing (Closes #36298)
  https://github.com/openclaw/openclaw/pull/36313

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
