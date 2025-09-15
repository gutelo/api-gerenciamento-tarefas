📌 API de Gerenciamento de Tarefas (Flask + JWT)

Esta é uma API REST desenvolvida com Flask para gerenciamento de tarefas, com autenticação de usuários usando JWT (JSON Web Token).
O projeto permite que cada usuário possa se cadastrar, fazer login e gerenciar suas próprias tarefas (CRUD).

🚀 Tecnologias utilizadas

Python

Flask

Flask-SQLAlchemy

Flask-JWT-Extended

SQLite (banco de dados local)

📁 Estrutura do Projeto
api-gerenciamento-tarefas/
│
├── app.py              # Arquivo principal do Flask
├── database.py         # Modelos e conexão com banco de dados
├── auth_routes.py      # Rotas de autenticação
├── task_routes.py      # Rotas das tarefas
├── requirements.txt    # Dependências do projeto
├── README.md           # Este arquivo
└── instance/
    └── tarefas.db      # Banco SQLite (criado automaticamente)

⚙️ Como executar o projeto
1. Clone o repositório:
git clone https://github.com/gutelo/api-gerenciamento-tarefas.git
cd api-gerenciamento-tarefas

2. Crie um ambiente virtual (opcional, mas recomendado):
python -m venv venv

Ative o ambiente:

# Linux/macOS:
source venv/bin/activate

# Windows:
venv\Scripts\activate

3. Instale as dependências:
pip install -r requirements.txt

4. Execute a aplicação:
python app.py

🧪 Testando a API e Respostas Esperadas usando [Postman](https://www.postman.com/downloads/)
1. Cadastro de usuário

Método: POST

Endpoint: http://127.0.0.1:5000/register

Body (JSON):

{
  "username": "usuario1",
  "email": "usuario1@email.com",
  "password": "123456"
}

Resposta (201):

{
  "msg": "Usuário registrado com sucesso"
}

2. Login do usuário

Método: POST

Endpoint: http://127.0.0.1:5000/login

Body (JSON):

{
  "email": "usuario1@email.com",
  "password": "123456"
}

Resposta (200):

{
  "access_token": "<jwt_token_aqui>",
  "user": {
    "id": 1,
    "username": "usuario1",
    "email": "usuario1@email.com"
  }
}

📌 Observação: pegue o token do /login e use no header de Create, Update e Delete.

3. Create Task

Método: POST

Endpoint: http://127.0.0.1:5000/tasks

Body (JSON):

{
  "title": "Estudar Flask",
  "description": "Finalizar projeto com autenticação"
}

Resposta esperada (201 Created)

{
  "msg": "Tarefa criada com sucesso",
  "id": 1
}

Obs: anote o id retornado — você usará ele nos testes de update/delete.

4. List Task (requer token JWT)

Método: GET

Endpoint: http://127.0.0.1:5000/tasks

Headers:

Authorization: Bearer <seu_token>

Resposta (200):

[
  {
    "id": 1,
    "title": "Estudar Flask",
    "description": "Finalizar projeto com autenticação",
    "completed": false
  }
]

5. Update Task

Método: PUT

Endpoint: http://127.0.0.1:5000/tasks/<task_id>

Body (JSON):

{
  "title": "Estudar Flask atualizado",
  "description": "Atualizei a descrição",
  "completed": true
}

Resposta esperada (200 OK)

{
  "msg": "Tarefa atualizada com sucesso"
}

6. Deletar uma tarefa

Método: DELETE

Endpoint: http://127.0.0.1:5000/tasks/<task_id>

Resposta esperada (200 OK)

{
  "msg": "Tarefa deletada com sucesso"
}

# Sequência de verificação rápida (fluxo completo)

POST /tasks → cria, retorna id = N.

GET /tasks → verifique que a tarefa aparece na lista.

PUT /tasks/N → atualizar campos.

GET /tasks → verifique que as alterações apareceram.

DELETE /tasks/N → deletar.

GET /tasks → verifique que a tarefa sumiu da lista.


✅ Contribuição

Sinta-se à vontade para clonar, modificar e testar o projeto. Sugestões são sempre bem-vindas! 🚀

📄 Licença

Este projeto está sob a licença MIT.