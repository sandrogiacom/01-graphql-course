# 01-graphql-course

Este projeto faz parte de um curso de GraphQL, utilizando Apollo Server para criar uma API robusta que consome dados de diferentes fontes, incluindo uma API REST (simulada pelo `json-server`) e um banco de dados MySQL (gerenciado com Knex).

## 🚀 Tecnologias

- [Node.js](https://nodejs.org/)
- [Apollo Server](https://www.apollographql.com/docs/apollo-server/)
- [GraphQL](https://graphql.org/)
- [Knex.js](https://knexjs.org/)
- [MySQL](https://www.mysql.com/)
- [JSON Server](https://github.com/typicode/json-server)
- [Docker](https://www.docker.com/)

## 📋 Pré-requisitos

Antes de começar, você vai precisar ter instalado em sua máquina:
- [Node.js](https://nodejs.org/en/) (recomenda-se versão LTS)
- [Docker](https://www.docker.com/) e [Docker Compose](https://docs.docker.com/compose/) (para o banco de dados)
- [Git](https://git-scm.com/)

## 🔧 Instalação e Configuração

1. Clone o repositório:
```bash
git clone git@github.com-luizomf:luizomf/01-graphql-course.git
cd 01-graphql-course
```

2. Instale as dependências:
```bash
npm install
```

3. Configure as variáveis de ambiente:
Crie um arquivo `.env` na raiz do projeto baseado no `.env-example`:
```bash
cp .env-example .env
```
Edite o arquivo `.env` e preencha com as informações necessárias (ex: `API_URL=http://localhost:3000`, `JWT_SECRET=seu_segredo`).
Além disso, certifique-se de configurar as variáveis de banco de dados no seu ambiente ou no arquivo `src/knex/knexfile.js` se necessário (elas são lidas do `process.env`).

Exemplo de variáveis necessárias:
```env
API_URL=http://localhost:3000
JWT_SECRET=seu_segredo_jwt
DATABASE_CLIENT=mysql
DATABASE_HOST=localhost
DATABASE_PORT=3306
DATABASE_NAME=graphql_mysql
DATABASE_USER=usuario
DATABASE_PASSWORD=senha
```

## 🐳 Banco de Dados (Docker)

O projeto utiliza MySQL. Você pode subir o container usando Docker Compose:
```bash
docker-compose up -d
```
Isso iniciará um container MySQL com as credenciais configuradas no `docker-compose.yml`.

### Migrations
Para criar as tabelas no banco de dados, execute as migrations do Knex:
```bash
npx knex migrate:latest --knexfile src/knex/knexfile.js
```

## 🏃 Executando o Projeto

### Modo de Desenvolvimento
Para rodar o projeto com recarregamento automático (nodemon) e o `json-server` simultaneamente, você pode abrir dois terminais:

**Terminal 1 (JSON Server):**
```bash
npm run server
```
O servidor de dados (REST API) rodará em `http://localhost:3000`.

**Terminal 2 (Apollo Server):**
```bash
npm run dev
```
O servidor GraphQL rodará em `http://localhost:4003`.

### Modo de Produção
Para compilar e rodar o projeto:
```bash
npm run build
npm start
```

## 🛠 Scripts Disponíveis

- `npm run dev`: Inicia o Apollo Server em modo de desenvolvimento com `nodemon` e `sucrase`.
- `npm run server`: Inicia o `json-server` para simular a API REST usando o arquivo `db.json`.
- `npm run build`: Limpa a pasta `dist` e compila o código fonte usando `sucrase`.
- `npm run start`: Inicia o `json-server` em background e executa o servidor compilado.

## 📄 Licença
Este projeto está sob a licença ISC.
