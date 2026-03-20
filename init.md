# Bootstrap Initialization Plan

このドキュメントは、MVP 開発前の初期構築を段階的に進めるための実行計画。
詳細チケットは `.github/tickets.md` を正として管理する。

## Skill 運用（.github）

- チケット追加・整理: `.github/ticket-creater/SKILL.md`
- チケット実装: `.github/ticket-implementer/SKILL.md`
- 実装レビュー: `.github/implement-reviewer/SKILL.md`
- 安全な改善: `.github/refactorer/SKILL.md`

## Bootstrap Scope

- 1. Repository structure
- 2. Docker local development
- 3. Go API skeleton
- 4. Next.js skeleton (App Router + TypeScript + ESLint)
- 5. Storybook setup
- 6. Playwright setup
- 7. OpenAPI contract file
- 8. Environment variable template

## Ticket Sequence

- [x] T-000 Repository scaffold
- [x] T-001 Docker Compose local environment (template)
- [x] T-020 Go API project skeleton (health endpoint)
- [x] T-030 Next app skeleton (manual scaffold)
- [x] T-040 Playwright setup (base config)
- [x] T-012 OpenAPI draft (`packages/contracts/openapi.yaml`)
- [x] .env template (`.env.example`)
- [x] T-004 Storybook command bootstrap verification
- [x] Dependency install and runtime verification (`docker compose up`, `npm install`, `go test`)

## Directory Baseline

```text
repo/

apps/
  api/
  web/

packages/
  contracts/

docs/
  ticket/

docker/

README.md
claude.md
```

## Web Frontend Layout

```text
apps/web/
  src/
    app/
    components/
    lib/
  test/
    unit/
    e2e/
```

## Execution Policy

- この段階では business logic を実装しない
- skeleton と運用ルールの固定のみ行う
- API path は `/api/v1` を維持する
- 追加ライブラリ導入は最小限にする

## Verification Log

1. `docker compose --env-file .env.example up --build -d`
2. `docker compose --env-file .env.example exec -T api go test ./...`
3. `docker compose --env-file .env.example exec -T web npm run lint`
4. `docker compose --env-file .env.example exec -T web npm run typecheck`
5. `docker compose --env-file .env.example exec -T web npm run test:unit`
6. `docker compose --env-file .env.example exec -T web npm run storybook:build`
7. `docker compose --env-file .env.example exec -T web npx playwright install chromium`
8. `docker compose --env-file .env.example exec -T web npx playwright install-deps chromium`
9. `docker compose --env-file .env.example exec -T web npm run test:e2e`

## Next Actions

1. API/Auth/Listings の実装チケット（Epic 2）に着手
2. OpenAPI から server/client 生成方針を決める
3. CI で Docker + unit/e2e を回すための workflow を追加
