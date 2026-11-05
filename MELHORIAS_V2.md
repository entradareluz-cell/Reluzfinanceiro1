# Melhorias V2 (revisão técnica)

## Correções (bugs confirmados em teste de navegador com API simulada)
1. `goalsData()` não existia: `render()` lançava ReferenceError e interrompia o carregamento após o login
   (sem botões Editar, sem dashboard/relatório atualizados). Função criada.
2. Botões "Excluir" (categorias e taxas) usavam `onclick` inline, mas `app.js` é módulo ES e as funções não são
   globais. Trocado por `data-action` + um único listener (também remove risco de XSS por id no atributo).
3. `advInit()` nunca rodava (`window.__reluzLoaded` nunca era definido): busca global, PDF anual e filtro do
   calendário não funcionavam. Agora inicia uma vez após o primeiro carregamento.
4. `setInterval` de 5 s re-renderizava calendário/relatórios continuamente. Removido; os painéis atualizam quando os dados mudam.
5. Data errada no Brasil: `toISOString()` usa UTC e, após 21h, "hoje" virava amanhã (e o mês virava o próximo no último dia).
   Criado `localISO()`.

## Melhorias
- Falha parcial de leitura não zera mais a tela: mantém dados anteriores e mostra aviso com "Tentar novamente".
  Se tudo falhar, mostra erro em vez de sistema vazio.
- Uma nova tentativa automática em leituras (`list`/`get`) após timeout/rede.
- Hover "levitando" removido de botões/nav (alinha com o próprio MOTION_AUDIT); foco visível para teclado.
- `deploy.yml`: valida sintaxe e publica só index/app/style (os .md internos não ficam públicos). Deve ficar em `.github/workflows/`.

## NÃO alterado (exige Issue própria — ver CONTEXTO_DO_PROJETO)
- `advGenerateRecurring()` segue desligado (grava no Sheets; risco de duplicar entre dispositivos).
- Autenticação (SHA-256 sem sal no navegador), `Code.gs` (não veio no zip), URL da API (difere do README).
