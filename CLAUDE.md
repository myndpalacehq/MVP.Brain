# MVP Brain

MVP Brain is a fork of [Noema](https://github.com/Guembri01/noema) (MIT), refocused on
**lead generation**. It is a self-hosted workspace where leads, companies, outreach and
follow-ups live in databases, and Claude Code works the pipeline through the built-in
MCP server at `/api/mcp` (see `docs/MCP.md`).

## Product focus

- Treat lead generation as the main use case when you design features, write copy,
  build templates or seed demo data: leads, prospects, companies, sources, pipeline
  stages, outreach sequences and follow-ups.
- Keep Noema's general workspace features working. Lead-gen features are added on
  top of them, not in place of them.

## Using the workspace from Claude Code

When the `mvp-brain` MCP server is connected:

- Use `list_databases` and `get_database_schema` to find the leads database and its
  properties before you query or write rows.
- Use `query_database_rows` with filters for questions like overdue follow-ups or
  uncontacted leads, rather than reading every row.
- Say which rows you plan to change before you bulk-update or archive leads.

## Working on the code

- Stack: Next.js 15, React 19, TypeScript, Tailwind v4, Prisma 6, PostgreSQL (docker
  container `noema-db`, port 5433), Tauri 2 for the desktop app.
- Quick gate: `npm run check:fast` (type check, lint, changed tests).
- The display name lives in `src/lib/project-info.ts`. Internal identifiers keep the
  `noema` prefix (`noema-db`, `noema_` tokens, `app.noema.desktop`, `NOEMA_*` env vars)
  so existing installs keep working. Don't rename them without a migration plan.
- Keep `LICENSE`, `AUTHORS.md` and the original authors' credit in `README.md` intact.
