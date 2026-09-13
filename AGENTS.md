# mailflare

Next.js 邮箱应用，使用 OpenNext 部署到 Cloudflare。应用在 `src/`，Worker 入口在 `worker.ts`，D1 迁移在 `drizzle/`。

- 使用 npm 和现有 `package-lock.json`。本地配置参考 `.dev.vars.example` 与 `wrangler.jsonc.example`，部署绑定以 `wrangler.jsonc` 为准。
- 保留邮箱、用户、邮件和会话数据；修改 schema 通过 Drizzle 生成并检查迁移，不直接重建远端库。
- `npm run db:migrate:local` 操作本地 D1；`npm run db:migrate:remote` 会写远端。`npm run deploy:with-migrations` 同时迁移和部署，按任务授权使用。
- 具体接入与部署说明按需查 [README](README.md) 和 `docs/`。不要从上游文档推断本机或线上绑定已经配置正确。

## 验证

`npm run build` 验证 Next.js 构建；Cloudflare 运行时差异用 `npm run preview` 检查。检查当前 Next.js 支持的 lint 命令后再使用 `npm run lint`，不能把不存在的命令算作通过。发送和转发邮件测试需要明确的收件人及发送授权。
