# Open PRs

- openclaw/openclaw#38239 config: warn when Feishu creds miskeyed under plugin config (Closes #38217)
  https://github.com/openclaw/openclaw/pull/38239
  - Summary: emit a targeted warning when users put Feishu appId/appSecret under plugins.entries.feishu-openclaw-plugin.config, pointing them to channels.feishu.
  - Tests: `pnpm -s vitest run --config vitest.unit.config.ts src/config/io.feishu-plugin-miskey.test.ts`

- clawbie/openclaw#8 fix(ui): render tool_result content blocks in tool cards (Closes #38223)
  https://github.com/clawbie/openclaw/pull/8
  - Summary: Control UI tool cards now extract tool_result output from OpenAI-style `content: [{ type: "text", text: ... }]`, preventing false "No output".
  - Tests: `cd ui && npx vitest run --config vitest.node.config.ts src/ui/chat/tool-cards.node.test.ts`
  - Note: unable to open PR against openclaw/openclaw due to GitHub API returning `User is blocked (createPullRequest)` for this account.

- openclaw/openclaw#38150 fix(cron): preserve sandbox defaults in isolated runs (Closes #38067)
  https://github.com/openclaw/openclaw/pull/38150
  - Summary: avoid shallow-merging agent `sandbox` overrides into `agents.defaults` during isolated cron runs, which could drop nested defaults like `sandbox.docker.dangerouslyAllowExternalBindSources`.
  - Tests: `npx --no-install vitest src/cron/isolated-agent/*.test.ts`

- clawbie/openclaw (pending) fix(venice): honor maxCompletionTokens from /models (Closes #38168)
  - Branch: https://github.com/clawbie/openclaw/tree/fix/venice-38168
  - Commit: 8baa79e0b
  - Summary: when Venice model discovery is enabled, prefer `model_spec.maxCompletionTokens` for both known catalog models and newly discovered ones to avoid hard-coded 8192 completion limits that can trigger HTTP 400.
  - Tests: `npx --no-install vitest run src/agents/venice-models.test.ts`
  - PR: NOT CREATED (GitHub API error: `User is blocked (createPullRequest)`)
  - Compare: https://github.com/openclaw/openclaw/compare/main...clawbie:fix/venice-38168

- clawbie/openclaw#6 fix(config): accept agents.list[].runtime in schema (Closes #38321)
  https://github.com/clawbie/openclaw/pull/6
  - Branch: https://github.com/clawbie/openclaw/tree/fix/runtime-38321
  - Commit: a2bd747ab
  - Summary: restore docs-vs-schema alignment by allowing `agents.list[].runtime` (per-agent ACP runtime defaults) in schema validation.
  - Tests: `npx --no-install vitest run --config vitest.unit.config.ts src/config/config.agent-runtime-schema.test.ts` ✅
  - Note: unable to open PR against openclaw/openclaw due to GitHub API returning `User is blocked (createPullRequest)` for this account.
  - Compare: https://github.com/openclaw/openclaw/compare/main...clawbie:fix/runtime-38321

- clawbie/openclaw#11 fix(systemd): treat user-bus unavailable as not enabled (Closes #38379)
  https://github.com/clawbie/openclaw/pull/11
  - Branch: https://github.com/clawbie/openclaw/tree/fix/systemd-is-enabled-38379
  - Commit: 3b42cf59e
  - Summary: treat "Failed to connect to bus" / missing user DBus session errors from `systemctl --user is-enabled` as "not enabled" so `openclaw onboard --install-daemon` can continue.
  - Tests: `./node_modules/.bin/vitest run src/daemon/systemd.test.ts` ✅
  - Note: unable to open PR against openclaw/openclaw due to GitHub API returning `User is blocked (createPullRequest)` for this account.
  - Compare: https://github.com/openclaw/openclaw/compare/main...clawbie:fix/systemd-is-enabled-38379

- clawbie/openclaw#5 fix(dotenv): expand env references in .env loading (Closes #38259)
  https://github.com/clawbie/openclaw/pull/5
  - Branch: https://github.com/clawbie/openclaw/tree/fix/dotenv-38259
  - Commit: 108c675be
  - Summary: expand `${VAR}` / `$VAR` references during dotenv loading while preserving shell env precedence and non-overriding semantics.
  - Tests: `pnpm -s vitest -c vitest.unit.config.ts src/infra/dotenv.test.ts`
  - Note: unable to open PR against openclaw/openclaw due to GitHub API returning `User is blocked` for this account.
  - Compare: https://github.com/openclaw/openclaw/compare/main...clawbie:openclaw:fix/dotenv-38259

- clawbie/openclaw#10 fix(chat.history): hide delivery-mirror transcript entries (Closes #38061)
  https://github.com/clawbie/openclaw/pull/10
  - Branch: https://github.com/clawbie/openclaw/tree/fix-chat-history-delivery-mirror-38061
  - Commit: 7d5e745a2
  - Summary: Gateway chat.history filters internal transcript entries (provider=openclaw, model=delivery-mirror) so webchat doesn’t show duplicate assistant replies.
  - Tests: `pnpm exec vitest run --config vitest.gateway.config.ts src/gateway/server.chat.gateway-server-chat.test.ts`
  - Note: unable to open PR against openclaw/openclaw due to GitHub API returning `User is blocked (createPullRequest)` for this account.
  - Compare: https://github.com/openclaw/openclaw/compare/main...clawbie:openclaw:fix-chat-history-delivery-mirror-38061

- openclaw/openclaw#37958 fix(telegram): use runtime config snapshot for SecretRef botToken (Closes #37909)
  https://github.com/openclaw/openclaw/pull/37958
  - Summary: prefer `getRuntimeConfigSnapshot()` for Telegram sends so SecretRef-backed `channels.telegram.botToken` is already resolved when tool-driven outbound paths call into telegram/send.
  - Tests: `pnpm -s vitest run src/telegram/send.test.ts src/telegram/token.test.ts`

- openclaw/openclaw#37809 fix: suppress Telegram NO_REPLY action envelope (Closes #37727)
  https://github.com/openclaw/openclaw/pull/37809
  - Summary: treat `{ "action": "NO_REPLY" }` as silent when parsing reply directives, preventing it from being delivered as literal JSON to end users.
  - Tests: `pnpm -s vitest -c vitest.unit.config.ts src/infra/outbound/payloads.test.ts`

- openclaw/openclaw#37938 fix(nextcloud-talk): avoid importing src/infra from bundled extension (Closes #37915) [CLOSED]
  https://github.com/openclaw/openclaw/pull/37938
  - Summary: avoid importing from ../../../src (not shipped in npm release) in the Nextcloud Talk extension, preventing plugin load crash.
  - Tests: `npx --no-install vitest run extensions/nextcloud-talk/src/channel.startup.test.ts`
  - Note (2026-03-07): PR was closed (unmerged); issue #37915 remains open.

- clawbie/openclaw (pending) fix(nextcloud-talk): avoid importing src/infra/abort-signal from bundled extension (Closes #37915)
  - Branch: https://github.com/clawbie/openclaw/tree/fix/nextcloud-talk-37915
  - Compare: https://github.com/openclaw/openclaw/compare/main...clawbie:fix/nextcloud-talk-37915
  - Commits: d5ad584c9, d3e55a277
  - Tests: `npx --no-install vitest run extensions/nextcloud-talk/src/wait-for-abort.test.ts`
  - PR: NOT CREATED (GitHub API error: `Validation Failed: user is blocked`)

- openclaw/openclaw#37559 fix(logging): rotate file logs after midnight for long-running gateway (Closes #37388)
  https://github.com/openclaw/openclaw/pull/37559
  - Summary: recreate subsystem child logger when the root file logger is rebuilt (daily rolling file), so logs switch to the new day without restarting.
  - Tests: `pnpm vitest run src/logging/subsystem.test.ts src/logging/logger-settings.test.ts src/logging/logger-env.test.ts src/logging/log-file-size-cap.test.ts --config vitest.unit.config.ts`

- openclaw/openclaw#37504 fix(delivery-recovery): stop retrying Telegram permanent Bad Request errors (Closes #37497)
  https://github.com/openclaw/openclaw/pull/37504
  - Summary: treat Telegram 400 errors like "message to be replied not found" / "message is too long" as permanent so delivery recovery moves them to failed/ instead of retrying forever.
  - Tests: `npx --no-install vitest run src/infra/outbound/outbound.test.ts`

- openclaw/openclaw#37492 fix(infra): classify wrapped 'fetch failed' as transient (Closes #37375)
  https://github.com/openclaw/openclaw/pull/37492
  - Summary: treat plain `Error` messages that include `fetch failed` as transient network errors so a single channel’s startup fetch failure (e.g. Discord gateway/bot fetch) won’t crash-loop the gateway.
  - Tests: `npx --no-install vitest run src/infra/unhandled-rejections.test.ts`

- openclaw/openclaw#37462 fix(cron): handle paginated cron.list response (Closes #37299)
  https://github.com/openclaw/openclaw/pull/37462
  - Summary: accept either a raw array (older gateway) or paginated response `{ jobs, total, ... }` for `openclaw cron list` to avoid CLI TypeError.
  - Tests: `pnpm test:fast src/cli/cron-cli/shared.test.ts`

- openclaw/openclaw#37575 fix(gateway): serve Control UI assets when installed via pnpm hardlinks (Closes #37455)
  https://github.com/openclaw/openclaw/pull/37575
  - Summary: allow hardlinked Control UI files (nlink > 1) inside the resolved control-ui root so pnpm global installs don't 404.
  - Tests: `pnpm -s vitest -c vitest.gateway.config.ts src/gateway/control-ui.http.test.ts`

- openclaw/openclaw#37419 fix(cli): keep stdout clean for --json commands (Closes #37323)
  https://github.com/openclaw/openclaw/pull/37419
  - Summary: route startup/plugin logs to stderr when `--json` is present so JSON output isn't corrupted.
  - Tests: `pnpm -s vitest run -c vitest.unit.config.ts src/cli/program/preaction.test.ts`, `pnpm -s vitest run -c vitest.unit.config.ts src/cli/program/json-mode.stderr-routing.test.ts`

- openclaw/openclaw#37348 fix(daemon): allow gateway install under sudo when user bus unavailable (Closes #37340)
  https://github.com/openclaw/openclaw/pull/37348
  - Summary: treat `systemctl --user is-enabled` "Failed to connect to bus" as "not enabled" so install/onboard can proceed.
  - Tests: `pnpm -s vitest run src/daemon/systemd.test.ts`

- openclaw/openclaw#37719 fix(process): wrap npm/npx .cmd via cmd.exe when npm-cli.js missing (Closes #37563)
  https://github.com/openclaw/openclaw/pull/37719
  - Branch: `fix/cli-37563`
  - Commit: `39908370f`
  - Summary: when npm/npx CLI script can't be resolved (e.g. nvm-windows/volta/fnm), fall back to executing the npm.cmd/npx.cmd shims via cmd.exe wrapper.
  - Tests: `node node_modules/vitest/vitest.mjs run src/process/exec.windows.test.ts`

- openclaw/openclaw#37754 fix(plugins): resolve secret refs in status report (Closes #37633)
  https://github.com/openclaw/openclaw/pull/37754
  - Summary: resolve secret-backed config fields (e.g. env var refs) before validating plugin connectivity and building the status report.
  - Tests: `pnpm test:fast -- src/plugins/status.test.ts`

- openclaw/openclaw#38043 fix(windows): npm pack works when Node path contains spaces (Closes #37563)
  https://github.com/openclaw/openclaw/pull/38043
  - Branch: `fix/windows-37563`
  - Commits: `9cb3f1aae`, `081676c4a`, `4e91169f0`
  - Summary: detect node.exe + npm-cli.js invocation and (when any argv contains whitespace) enable `windowsVerbatimArguments` and pre-quote args per CreateProcess rules to avoid argv mangling under `C:\\Program Files\\...`.
  - Tests: `pnpm exec vitest run src/process/exec.windows.test.ts`

- openclaw/openclaw#37646 fix(models): include config-injected models in --all list (Closes #37635)
  https://github.com/openclaw/openclaw/pull/37646
  - Summary: merge config-only provider models (from `models.providers.<provider>.models`) into the `--all` models list, even when missing from the underlying registry.
  - Tests: `pnpm -s vitest run src/commands/models/list.list-command.all-configured.test.ts`, `pnpm -s vitest run src/commands/models/list.list-command.forward-compat.test.ts`

- openclaw/openclaw#37292 fix(telegram): skip empty replies instead of crashing (Closes #37278)
  https://github.com/openclaw/openclaw/pull/37292
  - Summary: drop whitespace-only Telegram text replies so we never call sendMessage with empty text (prevents provider restarts).
  - Tests: not run (no node_modules here; no installs allowed)

- openclaw/openclaw#37858 docs: fix broken FAQ troubleshooting anchor (Closes #36970)
  https://github.com/openclaw/openclaw/pull/37858
  - Summary: fix Xfinity/Comcast SSL FAQ entry to link to `/help/troubleshooting` (remove non-existent anchor) to avoid dead navigation. Also sync the same fix in `docs/zh-CN/help/faq.md`.
  - Lightweight validation: `node -e "const fs=require('fs'); const p=['docs/help/faq.md','docs/zh-CN/help/faq.md']; for(const f of p){const s=fs.readFileSync(f,'utf8'); if(!s.includes('/help/troubleshooting')) throw new Error('missing troubleshooting link in '+f);} console.log('OK');"` ✅

- openclaw/openclaw#37308 docs: update claude-max-api-proxy links (Closes #20260)
  https://github.com/openclaw/openclaw/pull/37308
  - Tests: `npm test` (partial run; exited with SIGTERM; no failures reported before termination)

- openclaw/openclaw#37223 fix(tui): allow toggling deliver via /settings (Closes #37168)
  https://github.com/openclaw/openclaw/pull/37223
  - Tests: `pnpm -s vitest -c vitest.unit.config.ts src/tui/tui-command-handlers.test.ts`, `pnpm -s vitest -c vitest.unit.config.ts src/tui/tui-session-actions.test.ts src/tui/tui.test.ts`

- openclaw/openclaw#37236 fix(telegram): ignore non-numeric replyToMessageId (Closes #37222)
  https://github.com/openclaw/openclaw/pull/37236
  - Tests: `pnpm exec vitest run src/telegram/send.test.ts`

- openclaw/openclaw#37174 fix(media): resolve relative local media paths against allowed roots (Closes #37111)
  https://github.com/openclaw/openclaw/pull/37174
  - Tests: `pnpm -s vitest run -c vitest.config.ts src/web/media.test.ts`

- openclaw/openclaw#37254 fix(config): accept tools.web.fetch.firecrawl in schema (Closes #27833)
  https://github.com/openclaw/openclaw/pull/37254
  - Tests: `npx --no-install vitest run src/config/config.web-fetch-firecrawl-schema.test.ts --config vitest.unit.config.ts`

- openclaw/openclaw#37241 fix(docs): remove broken troubleshooting anchor for Xfinity SSL (Closes #36970)
  https://github.com/openclaw/openclaw/pull/37241
  - Tests: `node scripts/docs-link-audit.mjs`

- openclaw/openclaw#37281 fix(web_search): accept Brave zh-hans/zh-hant language codes (Closes #37260)
  https://github.com/openclaw/openclaw/pull/37281
  - Tests: `npx vitest run src/agents/tools/web-search.test.ts`

- openclaw/openclaw#37169 fix(skill-creator): validate allowed-tools frontmatter shape (Closes #37140)
  https://github.com/openclaw/openclaw/pull/37169
  - Tests: `python3 skills/skill-creator/scripts/test_quick_validate.py`

- openclaw/openclaw#37178 fix(tts): enable voice-bubble output for Matrix (Closes #37061)
  https://github.com/openclaw/openclaw/pull/37178
  - Tests: `pnpm -s vitest run --config vitest.unit.config.ts src/tts/tts.test.ts`

- openclaw/openclaw#37137 docs: fix broken FAQ troubleshooting anchor (Closes #36970)
  https://github.com/openclaw/openclaw/pull/37137
  - Tests: not run (docs-only one-line change)
  - Note: PR body already includes `Closes #36970`

- openclaw/openclaw#37122 docs(readme): update message send flag to --target (Closes #10458)
  https://github.com/openclaw/openclaw/pull/37122
  - Tests: `pnpm -s lint README.md`, `pnpm -s lint:docs README.md`, `pnpm -s docs:check-links`

- openclaw/openclaw#37102 docs(faq): fix broken Troubleshooting anchor link (Closes #36970)
  https://github.com/openclaw/openclaw/pull/37102
  - Branch: `fix/docs-faq-anchor-36970`
  - Commit: `f43d71f4b`
  - Tests: `node scripts/docs-link-audit.mjs`

- openclaw/openclaw#37029 fix(feishu): correct deliveryContext.to prefix (Closes #36987)
  https://github.com/openclaw/openclaw/pull/37029
  - Tests: `pnpm exec vitest -c vitest.extensions.config.ts extensions/feishu/src/bot.test.ts extensions/feishu/src/send-target.test.ts`

- openclaw/openclaw#37021 docs(claude-max-api-proxy): update repo links (Closes #20260)
  https://github.com/openclaw/openclaw/pull/37021
  - Tests: `node scripts/docs-link-audit.mjs`

- openclaw/openclaw#36998 docs(faq): remove broken troubleshooting link (Closes #36970)
  https://github.com/openclaw/openclaw/pull/36998
  - Tests: `pnpm -s lint:docs`

- openclaw/openclaw#36804 fix(models): don’t preserve baseUrl from existing models.json (Closes #36353)
  https://github.com/openclaw/openclaw/pull/36804
  - Tests: `pnpm -s vitest -c vitest.scoped-config.ts` (include: `src/agents/models-config.fills-missing-provider-apikey-from-env-var.test.ts`)

- openclaw/openclaw#36760 fix(discord): pass appliedTags through channel edit (Closes #36736)
  https://github.com/openclaw/openclaw/pull/36760
  - Update: move edits-channel test under unit runner (commit 0da933f93)

- openclaw/openclaw#36925 docs(session-logs): include archived .reset transcripts in globs (Closes #36799)
  https://github.com/openclaw/openclaw/pull/36925
  - Branch: `fix/session-logs-36799`

- openclaw/openclaw#36914 fix(podman): pass OPENCLAW_DOCKER_APT_PACKAGES to podman build (Closes #35397)
  https://github.com/openclaw/openclaw/pull/36914
  - Tests: `./test/setup-podman.apt-packages.test.sh`

- openclaw/openclaw#36350 fix(cron): persist payload.fallbacks on update (Closes #36263)
  https://github.com/openclaw/openclaw/pull/36350

- openclaw/openclaw#36298 fix(gateway): create transcript for chat.inject when missing (Closes #36170)
  https://github.com/openclaw/openclaw/pull/36298

- openclaw/openclaw#36959 fix(gateway): create transcript file for chat.inject when missing (Closes #36170)
  https://github.com/openclaw/openclaw/pull/36959
  - Branch: `fix/chat-inject-create-missing-36170`
  - Tests: `npx vitest -c vitest.gateway.config.ts run src/gateway/server-methods/chat.inject.create-if-missing.test.ts`

- openclaw/openclaw#35885 fix(browser): allow disabling AutomationControlled flag (Closes #35721)
  https://github.com/openclaw/openclaw/pull/35885
  - Update: add unit test + ensure `!--...` negation directive is not forwarded to Chrome.

- openclaw/openclaw#36814 fix(cron): harden cron store and run log file permissions (Closes #35881)
  https://github.com/openclaw/openclaw/pull/36814
  - Tests: `pnpm -s vitest -c vitest.unit.config.ts src/cron/store.test.ts src/cron/run-log.test.ts`

- openclaw/openclaw#35849 fix(config): accept openclaw browser driver in schema (Closes #35620)
  https://github.com/openclaw/openclaw/pull/35849

- clawbie/openclaw (pending) fix(voice-call): avoid outbound initial message race with streaming (Closes #36869)
  - Branch: https://github.com/clawbie/openclaw/tree/fix/voice-call-36869
  - Commit: 132a8fbf0
  - Tests: not run (node_modules missing; no installs allowed)
  - PR: NOT CREATED (gh auth unavailable in this environment)
  - Suggested create URL:
    https://github.com/openclaw/openclaw/compare/main...clawbie:fix/voice-call-36869?expand=1

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

- openclaw/openclaw#36437 fix(gateway): create missing transcript in chat.inject (Closes #36170)
  https://github.com/openclaw/openclaw/pull/36437

- openclaw/openclaw#36475 fix(tui): --deliver routes replies back to TUI (Closes #36088)
  https://github.com/openclaw/openclaw/pull/36475
  - Tests: `npm test -- --run src/gateway/server-methods/chat.tui-deliver-routing.test.ts`

- openclaw/openclaw#36496 fix(slack): propagate mediaLocalRoots for local uploads (Closes #36477)
  https://github.com/openclaw/openclaw/pull/36496
  - Tests: `pnpm -s vitest run src/agents/tools/slack-actions.test.ts`

- openclaw/openclaw#36523 fix(config): avoid RangeError in schema cache key (Closes #36508)
  https://github.com/openclaw/openclaw/pull/36523
  - Tests: `pnpm -s vitest -c vitest.unit.config.ts src/config/schema.test.ts`

- openclaw/openclaw#36562 daemon/systemd: accept is-enabled code 1 with not-found (Closes #36008)
  https://github.com/openclaw/openclaw/pull/36562
  - Tests: `npm test -- --run src/daemon/systemd.test.ts`

- openclaw/openclaw#36579 fix(gateway): create transcript file on chat.inject (Closes #36170)
  https://github.com/openclaw/openclaw/pull/36579
  - Tests: `pnpm -s vitest run --config vitest.gateway.config.ts src/gateway/server-methods/chat.inject.missing-transcript.test.ts`

- openclaw/openclaw#36691 fix(feishu): drop unsupported media timeout options (Closes #36581)
  https://github.com/openclaw/openclaw/pull/36691
  - Tests: `pnpm vitest extensions/feishu/src/media.test.ts --run`

- openclaw/openclaw#36733 fix(config): hash merged schema cache key to avoid RangeError (Closes #36508)
  https://github.com/openclaw/openclaw/pull/36733
  - Tests: `npx vitest run --config vitest.unit.config.ts src/config/schema.test.ts`

- openclaw/openclaw#37039 docs: fix broken Xfinity SSL troubleshooting anchor (Closes #36970)
  https://github.com/openclaw/openclaw/pull/37039
  - Status: OPEN (awaiting review)
  - Update: avoid bare URL for Xfinity reference + add missing Troubleshooting section anchor
  - Tests: `node scripts/docs-link-audit.mjs`

- openclaw/openclaw#37086 fix(tts): send Matrix TTS replies as voice bubbles (Closes #37061)
  https://github.com/openclaw/openclaw/pull/37086
  - Branch: `fix/tts-matrix-37061`
  - Commit: cfd5e7ea3
  - Tests: `npx --yes vitest -c vitest.unit.config.ts src/tts/tts.test.ts`

- openclaw/openclaw#37092 docs(faq): fix broken troubleshooting anchor for Xfinity SSL note (Closes #36970)
  https://github.com/openclaw/openclaw/pull/37092
  - Tests: `node scripts/docs-link-audit.mjs`
  - Update: rebased branch to latest upstream `main` (commit e7a4d7c)

- openclaw/openclaw#37434 fix(cron): avoid crash when cron.list returns malformed payload (Closes #37299)
  https://github.com/openclaw/openclaw/pull/37434
  - Summary: guard model column rendering against payloads missing `kind` / not being an object.
  - Tests: `pnpm vitest run --config vitest.unit.config.ts src/cli/cron-cli/shared.test.ts`

- openclaw/openclaw#37102 docs(faq): fix broken Troubleshooting anchor link (Closes #36970)
  https://github.com/openclaw/openclaw/pull/37102
  - Tests: `npx --yes markdownlint-cli2 docs/help/faq.md`

- openclaw/openclaw#36981 docs(faq): fix broken troubleshooting anchor for Xfinity SSL note (Closes #36970)
  https://github.com/openclaw/openclaw/pull/36981
  - Summary: Fixes dead FAQ link by pointing to /help/troubleshooting without a missing anchor.
  - Tests: not run (docs-only; vitest binary not available in this environment)

- openclaw/openclaw#37754 fix(plugins): resolve secrets for CLI plugin status (Closes #37633)
  https://github.com/openclaw/openclaw/pull/37754
  - Summary: buildPluginStatusReport now loads config with secret resolution enabled so env-backed SecretRef credentials don’t cause plugin registration errors in `openclaw plugins list`.
  - Tests: `npm test -- --config vitest.unit.config.ts src/plugins/status.test.ts`

- openclaw/openclaw#37858 docs: fix broken FAQ troubleshooting anchor (Closes #36970)
  https://github.com/openclaw/openclaw/pull/37858
  - Summary: remove broken cross-doc anchor from the Comcast/Xfinity SSL FAQ entry; link to /help/troubleshooting without a missing fragment.
  - Tests: not run (docs-only)
