# JD GitHub Actions 自动化模板

我查到当前较活跃的京东脚本仓库是 `6dylan6/jdpro`，最近一次提交时间为 2026-05-17。这个模板会在 GitHub Actions 中定时拉取它的 `main` 分支并运行你配置的脚本。

## 使用步骤

1. 新建一个私有 GitHub 仓库。
2. 把本目录里的 `.github/workflows/jdpro.yml` 放进该仓库。
3. 在仓库 `Settings -> Secrets and variables -> Actions -> Secrets` 添加：
   - `JD_COOKIE`：必填。多个账号用 `&` 或换行分隔，按脚本说明为准。
   - `PUSH_KEY`、`BARK_PUSH`、`TG_BOT_TOKEN`、`TG_USER_ID`：可选通知变量。
4. 可选：在 `Settings -> Secrets and variables -> Actions -> Variables` 添加 `JD_SCRIPT_LIST`，用空格分隔要运行的脚本，例如：

```text
jd_CheckCK.js jd_bean_info.js jd_signbeanact_.js jd_dpqd_sign.js jd_hssign.js jd_yssign.js
```

5. 到 `Actions -> JD automation -> Run workflow` 手动运行一次，确认日志正常。

## 注意

- 不要把 `JD_COOKIE` 写进仓库文件、Issue、Actions 日志或截图。
- 平台活动规则、验证码、风控和 Cookie 有效期会变化，失败时通常需要更新 Cookie 或调整脚本列表。
- 只建议用于你自己的账号。不要使用绕过验证码、批量账号、代理池或薅取平台补贴的配置。
- GitHub Actions 的定时任务使用 UTC，本模板默认每天北京时间 09:10 运行。
