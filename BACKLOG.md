# 📋 Backlog do Produto - UpDesk API (Melhoria)

Este documento é uma versão enriquecida do backlog original: adicionei colunas de Prioridade, Estimativa e Dependências, e incluí critérios de aceitação resumidos para cada história. Use prioridades P0 (crítico / Mínimo Produto Viável), P1 (alta), P2 (média) e P3 (baixa). Estimativas em pontos (Fibonacci curto).

---

### Legenda de Status
- `[ ]` **A Fazer:** A tarefa ainda não foi iniciada.
- `[/]` **Em Andamento:** A tarefa está sendo desenvolvida.
- `[x]` **Concluído:** A tarefa foi finalizada e entregue.

Observação: "Dependências" indica pré-requisitos relevantes para priorização/plano de sprints.

---

## 👤 Módulo 1: Gestão de Usuários e Autenticação

| ID | História de Usuário | Status | Prioridade | Estimativa | Dependências | Critérios de Aceitação (resumo) |
|---|---|:---:|:---:|:---:|:---:|---|
| **US001** | Como um **visitante**, eu quero **me cadastrar no sistema** fornecendo nome, e-mail e senha, para que eu possa abrir e acompanhar chamados. | `[ ]` | P0 | 3pts | — | POST /users aceita {name,email,password}; e-mail único; senha >=8; retorna 201 com usuário (sem senha); armazena senha segura (bcrypt/argon2); validação retorna 400. |
| **US002** | Como um **usuário cadastrado**, eu quero **fazer login** com meu e-mail e senha, para que eu possa acessar a plataforma. | `[ ]` | P0 | 3pts | US001 | POST /auth/login retorna JWT (access + refresh) ou 200; credenciais inválidas => 401; implementar bloqueio/brute-force básico. |
| **US003** | Como um **usuário logado**, eu quero **fazer logout** do sistema, para que eu possa proteger minha conta em dispositivos compartilhados. | `[ ]` | P1 | 2pts | US002 | POST /auth/logout revoga refresh token; torna access token inválido se usado com blacklist; retorna 204. |
| **US004** | Como um **usuário**, eu quero **recuperar minha senha** caso eu a esqueça, para que eu possa reaver o acesso à minha conta. | `[ ]` | P1 | 3pts | US001 | Flow: POST /auth/forgot -> envia token por e-mail; POST /auth/reset com token + nova senha; tokens expiram (ex: 1h); validação de senha; retorna 200. |

## 🎫 Módulo 2: Gestão de Chamados

| ID | História de Usuário | Status | Prioridade | Estimativa | Dependências | Critérios de Aceitação (resumo) |
|---|---|:---:|:---:|:---:|:---:|---|
| **US005** | Como um **usuário logado**, eu quero **abrir um novo chamado** preenchendo um título e uma descrição detalhada do problema, para que a equipe de suporte possa me ajudar. | `[ ]` | P0 | 3pts | US002 | POST /tickets com {title,description,attachments?}; título obrigatório; descrição >=20 chars; retorna 201 com id, status "open", timestamps; limitações de attachment aplicadas. |
| **US006** | Como um **usuário logado**, eu quero **visualizar uma lista com todos os meus chamados** abertos e seus respectivos status, para que eu possa acompanhar o andamento. | `[ ]` | P0 | 3pts | US002, US005 | GET /tickets?owner=current_user retorna lista paginada; inclui id, title, status, updated_at; filtros por status/periodo; paginação funcionando. |
| **US007** | Como um **usuário logado**, eu quero **adicionar comentários a um chamado existente**, para que eu possa fornecer informações adicionais à equipe de suporte. | `[ ]` | P1 | 2pts | US002, US005 | POST /tickets/{id}/comments com {text}; salva autor, timestamp; retorna 201; valida autorização (somente participantes e staff). |
| **US008** | Como um **usuário logado**, eu quero **marcar um chamado como "Resolvido"** caso o problema tenha sido solucionado, para que o ciclo de suporte seja encerrado. | `[ ]` | P1 | 2pts | US002, US005 | PATCH /tickets/{id}/status com status="resolved"; apenas autor do ticket ou admin/tecnico pode fechar; registra auditoria (quem, quando); retorna 200. |

## 🤖 Módulo 3: Integração com Inteligência Artificial

Observação: dividir em sub-histórias pequenas para entrega incremental — evitar bloqueio por dependência de provider externo.

| ID | História de Usuário | Status | Prioridade | Estimativa | Dependências | Critérios de Aceitação (resumo) |
|---|---|:---:|:---:|:---:|:---:|---|
| **US009** | Como um **usuário**, ao abrir um chamado, eu quero **interagir com um chat de IA** para refinar a descrição do meu problema, para que o chamado seja registrado com o máximo de detalhe. | `[ ]` | P2 | 5pts (dividir) | US005 | Dividir em: US009.1 (mock IA API) 2pts — endpoint /ai/suggest que retorna sugestões mock; US009.2 (UI básica) 3pts — integrar suggestions ao fluxo de criação; salvar interações. Requisitos: flag de feature; logs das sugestões. |
| **US010** | Como um **sistema**, eu quero **analisar o conteúdo de um novo chamado com a IA** para categorizá-lo e direcioná-lo automaticamente ao departamento correto, para que o tempo de triage seja reduzido. | `[ ]` | P2 | 5pts (dividir) | US005 | Dividir: US010.1 (análise básica de palavras-chave) 2pts — heurística local que sugere categoria; US010.2 (integração provider IA) 3pts — chamada assíncrona que atualiza ticket.category; categoria sugerida salva + confiança; fallback manual. |

## 📊 Módulo 4: Painel Administrativo e Relatórios

| ID | História de Usuário | Status | Prioridade | Estimativa | Dependências | Critérios de Aceitação (resumo) |
|---|---|:---:|:---:|:---:|:---:|---|
| **US011** | Como um **administrador**, eu quero **ter um painel para visualizar todos os chamados** de todos os usuários, para que eu tenha uma visão geral do suporte. | `[ ]` | P1 | 5pts | US006 | Painel com listagem paginada de tickets; filtros (status, técnico, período, categoria); export CSV simples; apenas roles admin/manager acessam. |
| **US012** | Como um **administrador**, eu quero **atribuir um chamado a um técnico ou departamento específico**, para que a responsabilidade pela resolução seja delegada. | `[ ]` | P1 | 3pts | US011 | PATCH /tickets/{id}/assignee com assignee_id; apenas admin/dispatcher pode atribuir; registra auditoria; notifica técnico (e-mail/notification). |
| **US013** | Como um **administrador**, eu quero **alterar o status de qualquer chamado** (Ex: Em Andamento, Pendente, Fechado), para que o fluxo de trabalho seja gerenciado. | `[ ]` | P1 | 3pts | US011 | PATCH /tickets/{id}/status com validação de workflow; registra histórico de status; notifica autor quando status muda para resolved/closed. |
| **US014** | Como um **administrador**, eu quero **gerar relatórios básicos** (ex: total de chamados por período, chamados por status), para que eu possa analisar a performance da equipe de suporte. | `[ ]` | P2 | 4pts | US011 | Endpoints /reports/overview que retornam métricas agregadas; filtros por período; cache/limitação para consultas pesadas; export CSV simples. |

---

Checklist de requisitos transversais (importante)
- Autorização e roles: visitante, usuário, técnico, administrador.
- Segurança: armazenamento seguro de senhas, proteção contra brute-force, validação de input (OWASP), CORS, rate-limiting básico.
- API: versionamento (ex: /api/v1), documentação OpenAPI/Swagger.
- Arquivos: limite e tipos para attachments; armazenamento (local vs S3).
- Observability: logs de auditoria para alterações críticas (status, atribuição), métricas básicas.
- Testes: cada história mínima com testes unitários e testes de integração importantes.
- Ambientes: feature flags para IA e integrações externas; usar mock em dev.
- E-mail/Notificações: filas (ex: enviar e-mail async), templates.

Formato sugerido para próximas entradas do backlog
- ID — Título — Prioridade — Estimativa — Dependências — Critérios de Aceitação (breve) — Observações

---

Próximo passo
Posso:
- Aplicar essas mudanças diretamente no arquivo BACKLOG.md do repositório (criar commit em nova branch) e abrir um PR;
- Ou gerar um template mais detalhado por história (com critérios completos e exemplos de payload) localmente para revisão.

Quer que eu aplique esta versão melhorada no BACKLOG.md do repositório (criar branch e PR)? Se sim, indique se prefere que eu:
- mantenha as descrições resumidas como estão aqui (bom para revisão rápida), ou
- escreva critérios de aceitação detalhados e payloads de API para cada história antes de commitar.
