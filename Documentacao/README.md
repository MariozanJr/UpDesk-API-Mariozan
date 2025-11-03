# Documentação da API — UpDesk

Esta pasta contém a documentação da API UpDesk: descrição dos endpoints, autenticação, modelos de dados, exemplos de uso, instruções para executar localmente e notas de versão.

Origem / referência do projeto:
- Repositório: https://github.com/MariozanJr/UpDesk-API-Mariozan
- README principal: https://github.com/MariozanJr/UpDesk-API-Mariozan/blob/bef46ba6f18451127452f62938ef35ee817b59d1/README.md

Sumário
- Visão Geral
- Autenticação
- Endpoints
- Modelos (schemas)
- Erros e códigos HTTP
- Execução local
- Testes
- Contribuição
- Changelog

---

## Visão Geral

A API UpDesk oferece funcionalidades para gerenciamento de chamados (tickets), usuários, categorias/departamentos e integração de IA para triagem e sugestão de soluções. Esta documentação descreve os recursos expostos, requisitos de autenticação e exemplos de requisições/respostas.

Base URL (exemplos)
- Desenvolvimento: http://localhost:3000
- Produção: (preencher URL de produção)

---

## Autenticação

A API utiliza tokens JWT (Bearer) para autenticação. Fluxo típico:
1. POST /auth/login — enviar email e senha.
2. Recebe-se um token JWT no campo `token`.
3. Incluir header em chamadas autenticadas:
   Authorization: Bearer <TOKEN>

Exemplo de login:
Request:
{
  "email": "usuario@exemplo.com",
  "password": "senha123"
}

Response:
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": { "id": 1, "name": "Nome Exemplo", "email": "usuario@exemplo.com" }
}

Tokens expirados devem retornar 401; implemente rota de refresh se necessário (ex.: /auth/refresh).

---

## Endpoints Principais (Resumo)

OBS: Substitua os exemplos por rotas reais conforme implementação do backend.

Autenticação
- POST /auth/register — cria usuário
- POST /auth/login — autentica e retorna token
- POST /auth/refresh — (opcional) renova token

Usuários
- GET /users — lista usuários (admin)
- GET /users/{id} — obtém usuário
- POST /users — cria usuário (admin)
- PUT /users/{id} — atualiza usuário
- DELETE /users/{id} — remove usuário

Tickets (Chamados)
- GET /tickets — lista tickets (filtros: status, user_id, page, per_page)
- GET /tickets/{id} — detalhes do ticket
- POST /tickets — cria novo ticket
- PUT /tickets/{id} — atualiza ticket (status, prioridade, atribuição)
- DELETE /tickets/{id} — exclui ticket
- POST /tickets/{id}/responses — adiciona resposta/comentário ao ticket

Categorias / Departamentos
- GET /categories
- POST /categories
- PUT /categories/{id}
- DELETE /categories/{id}

Integração IA (triagem / sugestão)
- POST /ia/suggest — envia texto do ticket e recebe sugestões de categorização/soluções

---

## Exemplos de Requisição / Resposta

Listar tickets (autenticado):
Request:
GET /tickets
Headers:
Authorization: Bearer <TOKEN>

Response 200:
[
  {
    "id": 1,
    "title": "Erro ao autenticar",
    "description": "Não consigo logar no sistema",
    "status": "open",
    "priority": "medium",
    "user_id": 3,
    "assigned_to": 2,
    "created_at": "2025-10-01T12:00:00Z"
  }
]

Criar ticket:
Request:
POST /tickets
Headers:
Authorization: Bearer <TOKEN>
Body:
{
  "title": "Problema X",
  "description": "Descrição do problema",
  "user_id": 3,
  "category_id": 1,
  "attachments": []
}
Response 201:
{
  "id": 12,
  "title": "Problema X",
  "status": "open",
  "created_at": "2025-10-30T09:00:00Z"
}

Sugestão IA:
Request:
POST /ia/suggest
Headers:
Authorization: Bearer <TOKEN>
Body:
{
  "text": "O usuário relata erro 500 ao salvar dados no sistema"
}
Response 200:
{
  "category": "Backend",
  "suggested_solution": "Verificar logs do servidor; validar payload de entrada",
  "confidence": 0.87
}

---

## Modelos (Schemas) — Exemplos

User
- id: integer
- name: string
- email: string
- role: string (admin, agent, user)
- created_at: datetime

Ticket
- id: integer
- title: string
- description: string
- status: string (open, pending, closed)
- priority: string (low, medium, high)
- user_id: integer
- assigned_to: integer | null
- category_id: integer
- created_at: datetime
- updated_at: datetime

Category
- id: integer
- name: string
- description: string

IA Suggestion
- category: string
- suggested_solution: string
- confidence: number (0.0 - 1.0)

---

## Códigos de Erro Comuns

- 200 OK — requisição bem sucedida
- 201 Created — recurso criado
- 400 Bad Request — parâmetros inválidos
- 401 Unauthorized — token ausente ou inválido
- 403 Forbidden — sem permissão
- 404 Not Found — recurso não encontrado
- 422 Unprocessable Entity — validação falhou
- 500 Internal Server Error — erro interno

Mensagens de erro devem retornar JSON no formato:
{
  "error": "Mensagem descritiva",
  "details": { "campo": ["erro1", "erro2"] }
}

---

## Execução Local

Pré-requisitos
- Node.js >= 14 (ou versão usada pelo projeto)
- Banco de dados (ex.: PostgreSQL, MS SQL) conforme configuração do projeto
- Docker (opcional)

Passos (exemplo Node):
1. Clone o repositório:
   git clone https://github.com/MariozanJr/UpDesk-API-Mariozan.git
2. Entre na pasta:
   cd UpDesk-API-Mariozan
3. Copie variáveis de ambiente:
   cp .env.example .env
   Preencha DATABASE_URL, JWT_SECRET, PORT e demais variáveis.
4. Instale dependências:
   npm install
5. Rode migrações (se houver):
   npm run migrate
6. Inicie o servidor em modo de desenvolvimento:
   npm run dev
7. Acesse: http://localhost:3000

Se o backend for em .NET/C#, ajuste comandos (dotnet restore / dotnet ef database update / dotnet run).

---

## Testes

Executar suíte de testes (exemplo):
npm test
ou, se for .NET:
dotnet test

---

## Contribuição

Fluxo sugerido:
1. Abra uma issue descrevendo o bug/feature.
2. Crie um branch a partir de main: docs/add-documentacao ou feature/<nome>.
3. Abra um PR descrevendo mudanças, incluindo testes.
4. Adicione revisores e aguarde aprovação.

Use formatos de commit semânticos e mantenha README atualizado.

---

## Changelog (sugestão)

Ver arquivo CHANGELOG.md nesta pasta.

---

## Contato

Para dúvidas e suporte: abrir issue no repositório ou contatar @MariozanJr no GitHub.
