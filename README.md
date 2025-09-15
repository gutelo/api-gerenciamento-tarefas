📌 API de Gerenciamento de Tarefas (Flask + JWT)
Esta é uma API REST desenvolvida com Flask para gerenciamento de tarefas, com autenticação de usuários usando JWT (JSON Web Token). O projeto permite que cada usuário se cadastre, faça login e gerencie suas próprias tarefas (CRUD).

🚀 Tecnologias utilizadas
Python

Flask

Flask-SQLAlchemy

Flask-JWT-Extended

SQLite (banco de dados local)


📁 Estrutura do Projeto
bash
Copiar
Editar
api-gerenciamento-tarefas/
│
├── app.py                # Arquivo principal do Flask
├── database.py           # Modelos e conexão com banco de dados
├── auth_routes.py        # Rotas de autenticação
├── task_routes.py        # Rotas das tarefas
├── requirements.txt      # Dependências do projeto
├── README.md             # Este arquivo
└── instance/
    └── tarefas.db        # Banco SQLite (criado automaticamente)


⚙️ Como executar o projeto

Clone o repositório:
bash
Copiar
Editar
git clone https://github.com/gutelo/api-gerenciamento-tarefas.git
cd api-gerenciamento-tarefas
Crie um ambiente virtual (opcional, mas recomendado):

bash
Copiar
Editar
python -m venv venv

# Linux/macOS
source venv/bin/activate

# Windows
venv\Scripts\activate
Instale as dependências:

bash
Copiar
Editar
pip install -r requirements.txt
Execute a aplicação:

bash
Copiar
Editar
python app.py


🧪 Como testar a API (usando Postman ou Insomnia)

1. Cadastro de usuário
Método: POST

Endpoint: /register

Body (JSON):

json
Copiar
Editar
{
  "username": "usuario1",
  "password": "123456"
}

2. Login do usuário
Método: POST

Endpoint: /login

Body (JSON):

json
Copiar
Editar
{
  "username": "usuario1",
  "password": "123456"
}
Retorno: Um token JWT para autenticação.

3. Listar tarefas (requer token JWT)
Método: GET

Endpoint: /tasks

Headers:

makefile
Copiar
Editar
Authorization: Bearer <seu_token>

4. Criar nova tarefa
Método: POST

Endpoint: /tasks

Body (JSON):

json
Copiar
Editar
{
  "title": "Estudar Flask",
  "description": "Finalizar projeto com autenticação"
}

5. Atualizar uma tarefa
Método: PUT

Endpoint: /tasks/<task_id>

Body (JSON):

json
Copiar
Editar
{
  "title": "Estudar Flask atualizado",
  "description": "Atualizei a descrição",
  "done": true
}

6. Deletar uma tarefa
Método: DELETE

Endpoint: /tasks/<task_id>

✅ Contribuição
Sinta-se à vontade para clonar, modificar e testar o projeto. Sugestões são sempre bem-vindas!

📄 Licença
Este projeto está sob a licença MIT.
