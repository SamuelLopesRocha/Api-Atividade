# 📘 API de Atividades

Este projeto é um microserviço desenvolvido em **Python** com **Flask**, responsável pelo gerenciamento de atividades e respostas dos alunos. Ele se integra à **API School System** para validações de turmas e alunos.

## 📦 Serviços Disponíveis

- **atividade/**: Gerenciamento (CRUD) de atividades.
- **resposta/**: Gerenciamento (CRUD) de respostas dos alunos.

## 🚀 Tecnologias Utilizadas

- Python
- Flask
- SQLite (banco de dados)
- Docker (conteinerização)

## ⚙️ Como Executar o Projeto Localmente

1. Instale as dependências (caso não utilize Docker):
```bash
pip install flask flask_sqlalchemy requests
```

2. Inicie os serviços com Docker Compose:

- Terminal 1 – API School System:
```bash
docker-compose up --build
```

- Terminal 2 – API de Atividades:
```bash
docker-compose up --build
```

### 🌐 Endpoints Ativos

- School System: [http://api_turma:8081](http://api_turma:8081)
- Atividade: [http://atividade:8080](http://atividade:8080)

## 📁 Estrutura do Projeto

```
atividade/
├── cliente/
├── controller/
├── model/
├── route/
├── config.py
├── app.py
├── Dockerfile
├── docker-compose.yml
└── requirements.txt
```

## 📌 Exemplos de Requisições

### 📝 Criar uma Nova Atividade

`POST /atividade`

```json
{
  "id_turma": 1,
  "enunciado": "Resolva a equação 2x + 3 = 7"
}
```

### 📋 Listar Todas as Atividades

`GET /atividade`

```json
[
  {
    "id": 1,
    "id_turma": 1,
    "enunciado": "Resolva a equação 2x + 3 = 7",
    "respostas": []
  }
]
```

### ✏️ Enviar Resposta de um Aluno

`POST /resposta/`

```json
{
  "id_atividade": 1,
  "id_aluno": 1,
  "resposta": "x = 2",
  "nota": 8.5
}
```

### 🔍 Listar Respostas de um Aluno

`GET /resposta/<aluno_id>`

```json
{
  "id": 1,
  "id_turma": 1,
  "enunciado": "Resolva a equação 2x + 3 = 7",
  "respostas": [
    {
      "id": 1,
      "id_aluno": 1,
      "resposta": "x = 2",
      "nota": 8.5
    }
  ]
}
```

### ✅ Validar Turma

`GET /atividade/validar_turma/<turma_id>`

```json
{
  "valida": true
}
```

### ✅ Validar Aluno

`GET /resposta/validar_aluno/<aluno_id>`

```json
{
  "valida": true
}
```
