# América Talentos Humanos

Site institucional e plataforma de recrutamento da **América Talentos Humanos**, empresa de RH e seleção de pessoal.

🔗 Site no ar: [americath.com.br](https://americath.com.br)

## O que o projeto faz

- **Site institucional** — apresentação da empresa, soluções de RH, diferenciais e canais de contato (WhatsApp).
- **Vagas abertas** (`vagas.html` / `vaga.html`) — listagem de vagas vindas do banco de dados, com busca e filtro por modalidade (presencial/híbrido/remoto), e página de detalhe por vaga.
- **Candidatura online** — formulário de candidatura com upload de currículo em PDF, gravado direto no banco de dados e no storage.
- **Modelo de currículo grátis** (`modelo-curriculo.html`) — página de conteúdo com dicas de currículo e um modelo `.docx` para download.
- **Painel RH** (`painel_rh.html`) — área interna autenticada para a equipe gerenciar vagas, candidatos e leads de empresas.
- **Notificação por e-mail** — trigger no banco que envia e-mail automático (via Resend) quando chega um novo candidato ou lead.
- **Página de privacidade / LGPD** (`privacidade.html`).

## Stack

- **Front-end**: HTML, CSS e JavaScript puros (sem framework, sem build step).
- **Back-end**: [Supabase](https://supabase.com) (Postgres + Auth + Storage + Row Level Security) para vagas, candidaturas, leads e autenticação do painel.
- **E-mail transacional**: Resend, disparado por trigger de banco via `pg_net`.
- **Hospedagem**: Netlify, com domínio próprio e certificado SSL automático.

## Estrutura

```
index.html            Página inicial
vagas.html / vaga.js   Listagem e detalhe de vagas
painel_rh.html         Painel administrativo interno
modelo-curriculo.html  Página de modelo de currículo
site.js                Lógica da página inicial e integração com Supabase
candidate-service.js   Envio de candidaturas (formulário + upload de currículo)
config.js              Configurações do site (WhatsApp, dados da organização)
*.sql                  Scripts de configuração do banco de dados (schema, políticas, triggers)
```

## Status

Site em produção, atendendo candidatos e empresas reais.
