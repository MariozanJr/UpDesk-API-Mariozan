# Endpoints da API — Detalhamento

Observação: ajuste os caminhos e parâmetros conforme a implementação real do backend.

1) Autenticação
- POST /auth/register
  - Body: { name, email, password, role }
  - Response: 201 { id, name, email }
- POST /auth/login
  - Body: { email, password }
  - Response: 200 { token, user }

2) Usuários
- GET /users
  - Query (opcional): page, per_page, role
  - Headers: Authorization
- GET /users/{id}
- POST /users
  - Body: { name, email, password, role }
- PUT /users/{id}
- DELETE /users/{id}

3) Tickets
- GET /tickets
  - Query: status, user_id, assigned_to, page, per_page
- GET /tickets/{id}
- POST /tickets
  - Body: { title, description, user_id, category_id, attachments }
- PUT /tickets/{id}
  - Body: { status, priority, assigned_to, comment }
- DELETE /tickets/{id}
- POST /tickets/{id}/responses
  - Body: { user_id, message }

4) Categorias
- GET /categories
- POST /categories
  - Body: { name, description }
- PUT /categories/{id}
- DELETE /categories/{id}

5) IA
- POST /ia/suggest
  - Body: { text }
  - Response: { category, suggested_solution, confidence }

Cada endpoint deve especificar:
- Permissões necessárias (ex.: admin, agent, user)
- Parâmetros obrigatórios e opcionais
- Exemplo de request/response
- Códigos de erro
