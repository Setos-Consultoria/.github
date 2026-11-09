# Setos Consultoria

## Onde cada coisa é publicada

| Repositório | O que é | Publicação |
|---|---|---|
| [setos-analises](https://github.com/Setos-Consultoria/setos-analises) | Análises para clientes e decisões internas | 🌐 **GitHub Pages** · https://setos-consultoria.github.io/setos-analises/ |
| setos-dashboard | Dashboard da Setos (privado, escopo a planejar) | 🔒 Não vai para o Pages · deploy próprio (a definir) |
| product-snack-front / api / infra | Snack: sistema para pequenos restaurantes | 🔒 Não vai para o Pages · deploy próprio (hospedagem a definir) |

**Regra:** só vai para o **GitHub Pages** o que é **site estático e público** (sem login, sem dados de cliente). Repositório publicado no Pages leva o tópico `github-pages` e a palavra **PUBLICADO** na descrição. O resto (APIs, apps com login, dashboards) gera imagem Docker e vai para o servidor.

## Workflows prontos (GitHub Actions)

Ficam em [`Setos-Consultoria/.github`](https://github.com/Setos-Consultoria/.github). Em qualquer repositório: **Actions › New workflow**, procure "Setos".

| Workflow | Para quê |
|---|---|
| Setos · Publicar no GitHub Pages | Site estático em repositório público |
| Setos · CI Node (pnpm) | Lint, typecheck, testes e build (com Postgres opcional) |
| Setos · Imagem Docker (ghcr.io) | Imagem do app pronta para o deploy no servidor |
