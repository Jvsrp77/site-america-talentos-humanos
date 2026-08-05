---
name: deploy-america-rh
description: Use sempre que o usuário pedir para publicar, subir, dar deploy, enviar ou "colocar no ar" alterações do site da América Talentos Humanos (site RHMaior) — mesmo que ele só diga "sobe isso" ou "publica". Garante que as mudanças foram testadas localmente antes de qualquer commit/push, e que o usuário aprovou o commit antes de ele acontecer.
---

# Deploy do site América RH

Este site ainda não tem deploy automático (sem remote configurado até o momento em que esta skill foi escrita) — "publicar" aqui significa, no mínimo, commitar as mudanças localmente, e possivelmente fazer push se/quando houver um remote configurado.

Siga esta ordem, sem pular etapas:

## 1. Teste localmente antes de qualquer coisa

O ambiente sandbox do assistente roda isolado — um servidor local iniciado pela ferramenta Bash/PowerShell do assistente **não é acessível pelo navegador real do usuário**. Portanto:

- Não tente validar a mudança abrindo um servidor você mesmo e checando via browser tool.
- Peça para o usuário rodar o servidor local dele mesmo, se ainda não estiver rodando:
  ```powershell
  cd "C:\Users\jrpin\OneDrive\Documentos\site RHMaior"; python -m http.server 8000
  ```
- Nunca sugira abrir o `index.html` direto por duplo-clique (`file://`) — o CSP da página bloqueia o carregamento do CSS e a página aparece sem estilo. Isso não é bug do site.
- Peça para o usuário confirmar visualmente que a alteração funciona como esperado antes de seguir para o commit.

## 2. Revise o que vai ser commitado

Antes de commitar, rode `git status` e `git diff` para conferir exatamente o que está mudando. Se aparecer algo inesperado (arquivo que você não tocou, credencial, dado sensível), pare e pergunte ao usuário antes de continuar.

## 3. Peça aprovação antes do commit

Nunca rode `git commit` sem o usuário confirmar explicitamente. Mostre um resumo do que vai entrar no commit e a mensagem proposta, e espere o "pode sim" antes de executar.

## 4. Push só se pedido e só se houver remote

Se o repositório ainda não tiver um remote configurado, avise o usuário em vez de tentar configurar um sozinho — a escolha de hospedagem (Netlify/Vercel/GitHub Pages/hospedagem tradicional) é decisão dele. Se já houver remote e o usuário pedir para subir, confirme o destino (branch/remote) antes do `git push`.
