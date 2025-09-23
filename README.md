# 🖥️ UpDesk-API-Mariozan
<p align="center">
  | <a href="#sobre-o-projeto">Sobre o Projeto</a> |
  <a href="#backlog-do-produto">Backlog do Produto</a> |
  <a href="#dordod">(DoR / DoD)</a> |
  <a href="#cronograma-de-evolucao">Cronograma de Evolução</a> |
  <a href="#tecnologias-utilizadas">Tecnologias</a> |
  <a href="#estrutura-de-pastas">Estrutura de Pastas</a> |  
  <br>  | <a href="#como-rodar-o-projeto">Como Rodar o Projeto</a> |  
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

# [📋 Backlog do Produto](./BACKLOG.md) <a id="backlog-do-produto"></a>
- [ ] Cadastro e login de usuários  
- [ ] Abertura de chamados  
- [ ] Chat com IA  
- [ ] Triagem automática de chamados  
- [ ] Painel administrativo  
- [ ] Relatórios de chamados

## 🎯 (DoR / DoD) <a id="dordod"></a>

Para garantir a qualidade e a consistência do desenvolvimento, nosso projeto segue uma **Definição de Ready (DoR)**, que é o checklist de critérios para uma tarefa poder ser iniciada, e uma **Definição de Done (DoD)**, que são os critérios para que uma tarefa seja considerada 100% concluída.  
Para ver a lista detalhada de critérios, acesse o documento completo:
**[📄 Acessar Definição de Pronto (DoR / DoD)](./DoR_DoD.md)**

# 📅 Cronograma de Evolução <a id="cronograma-de-evolucao"></a>

| Sprint          |    Período    | Documentação                                     |
| --------------- | :-----------: | ------------------------------------------------ |
| 🔖 **SPRINT 1** | 03/09 – 09/09| [Sprint 1 Docs](./sprint1.md) |
| 🔖 **SPRINT 2** | 10/09 – 16/09 | [Sprint 2 Docs](./sprint2.md) |
| 🔖 **SPRINT 3** | 17/09 – 23/09 | [Sprint 3 Docs](./sprint3.md) |


## 🚀 Tecnologias Utilizadas <a id="tecnologias-utilizadas"></a>  
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

 

# 🧑‍💻 Equipe <a id="equipe"></a>
| Nome                              | Papel         | GitHub                                  | LinkedIn                                               |
| --------------------------------- | ------------- | --------------------------------------- | ------------------------------------------------------ |
| Mariozan Damasceno Lacerda Júnior | Desenvolvedor | [GitHub](https://github.com/MariozanJr) | [LinkedIn](https://www.linkedin.com/in/mariozanjunior) |

