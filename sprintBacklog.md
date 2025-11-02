# 🗂️ Sprint Backlog

Este arquivo centraliza os arquivos de backlog e templates de sprint. Inclui a tabela de sprints e o template individual para cada sprint.

## 📋 Tabela de Sprints

Esta tabela complementa o cronograma (cronograma.md). Aqui há visão tática/operacional para cada sprint: objetivo, backlog principal, responsáveis e status. Use-a como template no planejamento de sprint e atualize a cada ciclo.

| Sprint | Período | Objetivo principal | Backlog / Itens-chave | Responsáveis | Status | Documentação |
| ------ | -------:| ------------------ | --------------------- | ------------ | ------ | ------------ |
| 🔖 **SPRINT 1** | 03/09 – 09/09 | Inicializar repositório, estrutura básica da API e CI | - Estrutura do projeto<br>- Configuração do linter/formatter<br>- Endpoint /health | Equipe inteira / MariozanJr | ✅ Concluído | [Sprint 1 Docs](./sprint1.md) |
| 🔖 **SPRINT 2** | 10/09 – 16/09 | Autenticação e modelos iniciais | - Modelos de usuário<br>- Cadastro / Login (JWT)<br>- Migrações iniciais | Backend: João / QA: Maria | ✅ Concluído | [Sprint 2 Docs](./sprint2.md) |
| 🔖 **SPRINT 3** | 17/09 – 23/09 | CRUD de tickets e prioridade de backlog | - Endpoints CRUD tickets<br>- Validação e testes básicos<br>- Documentação inicial da API | Backend: Ana / DevOps: Pedro | ✅ Concluído | [Sprint 3 Docs](./sprint3.md) |
| 🔖 **SPRINT 4** | 24/09 – 30/09 | Integração com sistema de notificações e logs | - Notificações por e-mail (serviço mock)<br>- Logging centralizado (estrutura)<br>- Testes de integração básicos | Backend: Ana / DevOps: Pedro | ⏳ Em planejamento | [Sprint 4 Docs](./sprint4.md) |
| 🔖 **SPRINT 5** | 01/10 – 07/10 | Paginação, filtros e melhorias de performance | - Paginação nos endpoints de lista<br>- Filtros por status/prioridade<br>- Análise e melhorias simples de query | Equipe: João, Ana | ⏳ Em planejamento | [Sprint 5 Docs](./sprint5.md) |
| 🔖 **SPRINT 6** | 08/10 – 14/10 | Segurança e hardening | - Revisão de permissões/roles<br>- Proteção contra ataques comuns (rate limit, validações)<br>- Revisão dependências de segurança | Security: Equipe / DevOps | ⏳ Em planejamento | [Sprint 6 Docs](./sprint6.md) |
| 🔖 **SPRINT 7** | 15/10 – 21/10 | Preparação para release (v1.0) | - Testes end-to-end<br>- Documentação da API (OpenAPI/Swagger)<br>- Pipeline de release | Equipe inteira | ⏳ Em planejamento | [Sprint 7 Docs](./sprint7.md) |
| 🔖 **SPRINT 8** | 22/10 – 28/10 | Release e estabilização pós-lançamento | - Deploy para produção (canary/blue-green se aplicável)<br>- Correções críticas pós-release<br>- Monitoramento ativo | DevOps / Suporte | ⏳ Em planejamento | [Sprint 8 Docs](./sprint8.md) |

## Template de Sprint (copiar para cada sprint_x.md)
---
Sprint: SPRINT N  
Período: dd/mm – dd/mm  
Objetivo: (frase curta)  
Backlog principal:
- História #123 — Título — Pontos — Responsável — Status
- História #124 — Título — Pontos — Responsável — Status

Critérios de aceitação:
- [ ] Critério 1
- [ ] Critério 2

Definições de pronto (DoD) aplicáveis:
- Código revisado e aprovado
- Testes unitários com cobertura mínima X%
- Documentação atualizada (README / OpenAPI)

Impedimentos / Riscos:
- (descrever)

Notas de planejamento:
- Estimativa de capacidade: X pontos
- Observações sobre dependências externas

Como usar
- Antes do Planning: preencher Objetivo e Backlog principal com o Product Owner.
- No Planning: dividir histórias em tarefas e estimar (pontos/h).
- Durante a Sprint: atualizar Status e registrar impedimentos.
- Na Review: linkar PRs e marcar itens concluídos.
- Na Retrospectiva: agregar ações para a próxima sprint.

---

Arquivos sugeridos a criar (opcional): sprint4.md, sprint5.md, sprint6.md, sprint7.md, sprint8.md