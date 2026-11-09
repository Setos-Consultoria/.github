# .github

Padrões compartilhados por **todos os repositórios da Setos Consultoria**.

| Pasta | O que tem |
|---|---|
| `.github/ISSUE_TEMPLATE/` | Templates de issue: Épico, História, Tarefa, Bug |
| `.github/workflows/` | **Workflows reutilizáveis** (cada repositório chama com `uses:`) |
| `workflow-templates/` | Modelos que aparecem em **Actions › New workflow** de qualquer repositório da organização |
| `profile/README.md` | Página inicial da organização no GitHub (o que é publicado onde) |

## Publicação: GitHub Pages ou não?

- **GitHub Pages** → só **site estático e público** (sem login, sem dados de cliente). O repositório precisa ser **público** (plano gratuito). Marque com o tópico `github-pages` e escreva **PUBLICADO** na descrição.
- **Fora do Pages** → APIs, apps com login, dashboards e tudo que é privado. Usam CI + imagem Docker; o deploy no servidor depende da hospedagem (decisão em aberto).

Os dois tipos usam GitHub Actions.

## Workflows reutilizáveis

### `pages.yml`: publicar no GitHub Pages

```yaml
name: Publicar no GitHub Pages
on:
  push: { branches: [main] }
  workflow_dispatch:
permissions: { contents: read, pages: write, id-token: write }
jobs:
  pages:
    uses: Setos-Consultoria/.github/.github/workflows/pages.yml@main
    # with: { build-command: pnpm build, output-dir: dist }
```

Primeira vez: `gh api -X POST repos/Setos-Consultoria/<repo>/pages -f build_type=workflow`.

### `ci-node.yml`: CI Node/TypeScript com pnpm

```yaml
name: CI
on:
  pull_request:
  push: { branches: [main] }
jobs:
  ci:
    uses: Setos-Consultoria/.github/.github/workflows/ci-node.yml@main
    with:
      scripts: lint typecheck test build   # scripts que não existirem são pulados
      postgres: true                       # opcional: Postgres 16 + DATABASE_URL
```

### `docker-image.yml`: imagem Docker no ghcr.io

```yaml
name: Imagem Docker
on:
  push: { branches: [main] }
permissions: { contents: read, packages: write }
jobs:
  image:
    uses: Setos-Consultoria/.github/.github/workflows/docker-image.yml@main
```

Gera `ghcr.io/setos-consultoria/<repo>:latest` e `:<sha>`.

## Regras

- Mudança aqui afeta **todos** os repositórios que usam `@main`: abra PR e teste num repositório antes.
- Este repositório é **público** (exigência do GitHub para compartilhar templates). Nada de segredos aqui; segredos ficam em *Settings › Secrets* de cada repositório ou da organização.
