# 🔖 Documentação da Sprint 3

**Período:** 17/09/2025 – 23/09/2025

---

## 🎯 Meta da Sprint

A meta desta Sprint foi **modelar o comportamento dinâmico e as interações chave do sistema**. O foco foi a criação do **Diagrama de Sequência** para a funcionalidade mais crítica: a abertura de um novo chamado, detalhando a comunicação entre as camadas da aplicação.

## 📋 Itens do Backlog Planejados

- **[DG003]** - Diagrama de Sequência - Abertura de Novo Chamado.
- **[US009]** - Implementar a integração com o chat da IA.

## ✅ Itens Entregues

- **Diagrama de Sequência da Abertura de Chamado foi concluído.** O diagrama ilustra o fluxo de eventos desde a requisição do usuário na View, passando pela lógica na Controller, até a persistência dos dados pela Model no banco.
- A integração com a API de IA foi testada e o fluxo de triagem automática foi validado, conforme modelado no diagrama.

## 🔍 Revisão e Retrospectiva

- **O que foi bem:** O Diagrama de Sequência foi fundamental para identificar e corrigir uma falha na lógica de validação de dados antes mesmo da implementação final.
- **O que pode melhorar:** A documentação da API da IA não estava clara, o que causou um pequeno atraso.
- **Ações a tomar:** Sempre validar a documentação de APIs de terceiros no início da Sprint.
