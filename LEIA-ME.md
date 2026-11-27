# Unique Obras — implantação

**Estrutura:** `index.html` + `config.js` + `sw.js` + `manifest` + ícones = app (GitHub Pages). `api/worker.js` = backend (Cloudflare Worker, grátis). Dados ficam em um repositório GitHub **privado** separado.

1. Crie o repositório privado `unique-dados` e um token GitHub (fine-grained, só esse repo, permissão *Contents: read/write*).
2. `cd api && npx wrangler deploy` e depois, um por um, `npx wrangler secret put <NOME>`:
   `NVIDIA_API_KEY`, `GH_TOKEN`, `TRELLO_KEY`, `TRELLO_TOKEN`, `JWT_SECRET` (texto aleatório longo), `SEED_ADMIN_PASSWORD` (senha inicial da Silvana).
3. Edite `wrangler.toml` (repo, origem) e `config.js` (URL do Worker).
4. Publique a pasta (sem `api/`) no GitHub Pages → abra no celular → "Adicionar à tela inicial" (iOS: Safari › Compartilhar; Android: Chrome › Instalar).
5. Novas versões: suba os arquivos e aumente `V` em `sw.js`; os aparelhos se atualizam sozinhos.

Notas: diários são mesclados por `id` (ninguém sobrescreve ninguém); sem internet, o app usa os dados salvos no aparelho e sincroniza ao voltar; fotos continuam só na sessão (não vão ao GitHub).
