# Reluz Financeiro

Sistema financeiro web (HTML + JS + CSS) com Google Sheets como banco de dados e Google Apps Script como API.

- Acesso: `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/` (após o primeiro deploy)
- A API é configurada em `app.js` (constante `API_URL`). O `Code.gs` fica no seu projeto do Apps Script.
- Documentação interna e regras de trabalho: pasta `docs/` (comece por `docs/CONTEXTO_DO_PROJETO.md`).

## Como publicar (uma vez)
1. Crie um repositório no GitHub e envie estes arquivos (inclusive a pasta oculta `.github`).
2. Em **Settings → Pages → Build and deployment → Source**, escolha **GitHub Actions**.
3. Em **Actions**, aguarde o workflow "Deploy to GitHub Pages" ficar verde. O link aparece nele.

## Como atualizar
Altere os arquivos no GitHub (ou envie por git) na branch `main`. O deploy roda sozinho.

## Observações
- GitHub Pages em repositório **privado** exige plano pago; em repositório público é grátis.
- O deploy publica apenas `index.html`, `app.js` e `style.css`.
- Qualquer pessoa com o link vê o front-end; os dados só abrem com login (validado no Apps Script).
