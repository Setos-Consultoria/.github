# .github (Setos Consultoria): instruções para o agente

Repositório de padrões da organização, **público** e usado por todos os repositórios. Leia o README antes.

- `.github/workflows/*.yml` são workflows **reutilizáveis** (`on: workflow_call`). Repositórios chamam com `uses: Setos-Consultoria/.github/.github/workflows/<arquivo>@main`, então qualquer mudança afeta todos: mantenha os `inputs` compatíveis (só adicione inputs novos com default) e abra PR.
- `workflow-templates/` tem os modelos do botão "New workflow": cada `.yml` precisa de um `.properties.json` com o mesmo nome.
- Regra de publicação: **GitHub Pages só para site estático e público**; o resto vai por CI + imagem Docker (hospedagem ainda a definir: pergunte, não invente).
- Nunca coloque segredos aqui. Textos em português do Brasil.
