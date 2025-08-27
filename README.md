# 🖥️ UpDesk-API-Mariozan
<p align="center">
  | <a href="#sobre-o-projeto">Sobre o Projeto</a> |
  <a href="#backlog-do-produto">Backlog do Produto</a> |
  <a href="#cronograma-de-evolucao">Cronograma de Evolução</a> |
  <a href="#sprints">Sprints</a> |
  <a href="#tecnologias-utilizadas">Tecnologias</a> |
  <a href="#estrutura-de-pastas">Estrutura de Pastas</a> |  
  <a href="#como-rodar-o-projeto">Como Rodar o Projeto</a> |  
   <br> | <a href="#documentacao">Documentação</a> |  
  <a href="#equipe">Equipe</a> |
</p>


# 📖 Sobre o Projeto <a id="sobre-o-projeto"></a>
Projeto UpDesk – versão individual aplicada no PIM/API  
Disciplina: Projeto de Sistemas Orientado a Objetos  
<br>
O UpDesk é um projeto acadêmico focado no desenvolvimento de um sistema de abertura de chamados com suporte de inteligência artificial.
O sistema oferece:  
✔ Interface web responsiva  
✔ Gerenciamento de chamados  
✔ Chat com IA para triagem  
✔ Direcionamento automatizado de solicitações   

# 📋 Backlog do Produto
- [ ] Cadastro e login de usuários  
- [ ] Abertura de chamados  
- [ ] Chat com IA  
- [ ] Triagem automática de chamados  
- [ ] Painel administrativo  
- [ ] Relatórios de chamados

# 📅 Cronograma de Evolução

| Fase / Sprint | Período        | Atividades Principais                                                                    |
| ------------- | -------------- | ---------------------------------------------------------------------------------------- |
| Planejamento  | 26/08 – 02/09  | Definição do backlog, levantamento de requisitos, configuração inicial do repositório   |
| Sprint 1      | 03/09 – 09/09  | Estrutura inicial do projeto, configuração do banco de dados, criação das primeiras telas|
| Sprint 2      | 10/09 – 16/09  | Implementação da abertura de chamados e integração com banco                             |
| Sprint 3      | 17/09 – 23/09  | Integração do chat com IA, testes de triagem automática                                  |
| Sprint 4      | 24/09 – 30/09  | Painel administrativo, relatórios, ajustes finais e entrega do incremento               |


# 🚀 Sprints
| Sprint   | Período       | Documentação         | Vídeo no YouTube |
| -------- | ------------- | -------------------- | ---------------- |
| Sprint 1 | 03/09 – 09/09 | [Doc Sprint 1](link) | [Vídeo](link)    |
| Sprint 2 | 10/09 – 16/09 | [Doc Sprint 2](link) | [Vídeo](link)    |
| Sprint 3 | 17/09 – 23/09 | [Doc Sprint 1](link) | [Vídeo](link)    |
| Sprint 4 | 24/09 – 30/09 | [Doc Sprint 2](link) | [Vídeo](link)    |


## 🚀 Tecnologias Utilizadas  
- **Backend**: Python + Flask  
- **Frontend**: HTML, CSS, JavaScript  
- **Banco de Dados**: SQL (MySQL ou MS SQL Server)  
- **Prototipagem**: Figma  
- **Controle de Versão**: Git / GitHub 

# 🗂 Estrutura de Pastas <a id="estrutura-de-pastas"></a>
📁 app/                   # Pasta principal da aplicação  
 ┣ 📁 templates/          # Arquivos HTML (renderizados pelo Flask)  
 ┣ 📁 static/             # Arquivos estáticos (CSS, JS, imagens)  
 ┣ 📁 models/             # Classes e entidades do sistema (POO)  
 ┣ 📁 routes/             # Definição das rotas/endpoints do Flask  
 ┗ 📁 utils/              # Funções auxiliares (integração IA, helpers, etc.)  
   
📁 database/              # Configurações e scripts do banco de dados  
 ┗ 📄 schema.sql          # Estrutura inicial do banco de dados (DDL)  
  
📄 app.py                 # Arquivo principal da aplicação (ponto de entrada)  
📄 requirements.txt       # Lista de dependências Python do projeto  



# 🧑‍💻 Como Rodar o Projeto <a id="como-rodar-o-projeto"></a>
Pré-requisitos:
- Python 3.x  
- Pip
- SQL Server ou MySQL
- IDE ou editor (VS Code, PyCharm, etc.)  

## Clonar o repositório  
git clone https://github.com/MariozanJr/UpDesk-API-Mariozan.git   
cd UpDesk-API-Mariozan   

### Instalar dependências  
pip install -r requirements.txt  

### Configurar banco de dados e criar tabelas necessárias  

### Executar a aplicação  
python app.py  

# 📚 Documentação <a id="documentacao"></a>
### 📂 Acesse a pasta de Documentação

Inclui:
- Manual do Usuário
- Checklist de DoR (Definition of Ready) e DoD (Definition of Done)
- Documentos de cada Sprint
 

# 🧑‍💻 Equipe <a id="Equipe"></a>
| Nome                              | Papel         | GitHub                                  | LinkedIn                                               |
| --------------------------------- | ------------- | --------------------------------------- | ------------------------------------------------------ |
| Mariozan Damasceno Lacerda Júnior | Desenvolvedor | [GitHub](https://github.com/MariozanJr) | [LinkedIn](https://www.linkedin.com/in/mariozanjunior) |

