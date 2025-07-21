Aplicação para Gerenciamento de Livros e Autores
Este repositório contém o código-fonte de uma aplicação web para o cadastro de livros e seus respectivos autores. O projeto foi concebido como parte da avaliação da disciplina TAD0203 - Gestão da Qualidade de Software e demonstra a aplicação da arquitetura MVC, além de uma suíte completa de testes.

🎯 Objetivo

O principal objetivo deste projeto é a construção de uma aplicação web que segue a arquitetura MVC, oferecendo duas telas de cadastro (para livros e autores) com os dados persistidos em um banco PostgreSQL. Um foco central foi a aplicação de uma estratégia de testes robusta, cobrindo:

Testes de Unidade/Integração: Para garantir a confiabilidade de todos os endpoints da API (operações CRUD).

Testes de Ponta a Ponta (E2E): Utilizando Cypress para validar o comportamento e a interação nas interfaces de usuário (views).

🛠️ Tecnologias Utilizadas

Backend: Node.js, Express

Banco de Dados: PostgreSQL

Frontend: HTML, CSS (Bootstrap 5), JavaScript

Template Engine: EJS

Testes:

Jest & Supertest (Testes Unitários e de Integração)

Cypress (Testes E2E)

📁 Estrutura do Projeto

A organização dos arquivos segue uma estrutura lógica para facilitar a manutenção e escalabilidade:

projeto-gqs-livros-autores/
├── src/
│   ├── controllers/          # Lógica de controle (MVC)
│   │   ├── autorController.js
│   │   └── livroController.js
│   ├── models/              # Modelagem de dados (MVC)
│   │   ├── Autor.js
│   │   └── Livro.js
│   ├── routes/              # Definição das rotas
│   │   ├── autorRoutes.js
│   │   └── livroRoutes.js
│   ├── views/               # Camada de apresentação (MVC)
│   │   ├── autores/
│   │   │   └── novo.ejs
│   │   ├── livros/
│   │   │   └── novo.ejs
│   │   ├── layout.ejs
│   │   └── index.ejs
│   ├── public/              # Arquivos estáticos (CSS, JS, imagens)
│   └── database/            # Scripts e conexão com o BD
│       ├── connection.js
│       └── init.sql
├── tests/
│   ├── unit/                # Testes de unidade
│   │   ├── autor.test.js
│   │   └── livro.test.js
│   └── integration/         # Testes de integração
│       ├── autor.integration.test.js
│       └── livro.integration.test.js
├── cypress/
│   └── e2e/                 # Testes de ponta a ponta
│       ├── autor.cy.js
│       └── livro.cy.js
├── app.js                   # Ponto de entrada da aplicação
├── package.json
├── cypress.config.js
├── .env                     # Arquivo para variáveis de ambiente
└── README.md
🚀 Instalação e Configuração

Pré-requisitos:

Node.js (v14 ou superior)

PostgreSQL (v12 ou superior)

NPM ou Yarn

1. Clone o repositório:

Bash

git clone <url-do-repositorio>
cd projeto-gqs-livros-autores
2. Instale as dependências do projeto:

Bash

npm install
3. Configure o Banco de Dados:

Garanta que seu serviço PostgreSQL esteja ativo.

Crie o banco de dados e as tabelas executando o script SQL.

Bash

# Conecte-se ao psql com um superusuário (ex: postgres)
psql -U postgres

# Dentro do psql, execute o script para criar o banco e as tabelas
\i src/database/init.sql

# Alternativamente, execute o comando manualmente:
CREATE DATABASE livros_autores_db;
Renomeie o arquivo .env.example para .env e preencha com suas credenciais:

Snippet de código

DB_HOST=localhost
DB_PORT=5432
DB_NAME=livros_autores_db
DB_USER=postgres
DB_PASSWORD=sua_senha_aqui
PORT=3000
4. Inicie o servidor:

Bash

# Para ambiente de desenvolvimento com hot-reload
npm run dev

# Para ambiente de produção
npm start
A aplicação estará rodando em http://localhost:3000.

🧪 Executando os Testes

Testes Unitários e de Integração com Jest:

Bash

# Rodar a suíte completa de testes
npm test

# Rodar os testes em modo de observação (watch)
npm run test:watch

# Rodar os testes e gerar um relatório de cobertura
npm run test:coverage
Testes E2E com Cypress:

Atenção: A aplicação deve estar em execução (npm run dev ou npm start) para que os testes E2E funcionem.

Bash

# Abrir a interface gráfica do Cypress
npm run cypress:open

# Executar os testes em modo headless (via terminal)
npm run cypress:run
📋 Funcionalidades

API Endpoints:

Autores:

GET /api/autores - Retorna todos os autores.

GET /api/autores/:id - Retorna um autor específico.

POST /api/autores - Cria um novo autor.

PUT /api/autores/:id - Atualiza um autor existente.

DELETE /api/autores/:id - Remove um autor.

Livros:

GET /api/livros - Retorna todos os livros.

GET /api/livros/:id - Retorna um livro específico.

POST /api/livros - Cria um novo livro.

PUT /api/livros/:id - Atualiza um livro existente.

DELETE /api/livros/:id - Remove um livro.

Interface Web (Views):

/ - Página de boas-vindas.

/autores/novo - Formulário para registrar um novo autor.

/livros/novo - Formulário para registrar um novo livro.

🧪 Cobertura de Testes

O projeto possui uma estratégia de testes completa, incluindo:

Testes Unitários: Focados na validação dos modelos Autor e Livro, cobrindo cenários de sucesso, falhas, dados obrigatórios e tratamento de exceções.

Testes de Integração: Validam todos os endpoints da API, incluindo respostas de sucesso (2xx), erros do cliente (4xx) e erros do servidor (5xx), além de verificar o relacionamento entre as entidades.

Testes E2E: Simulam a jornada do usuário final, cobrindo a navegação entre as telas, o preenchimento de formulários e a verificação de mensagens de feedback na interface.

🔧 Scripts Disponíveis

npm start: Inicia o servidor em modo de produção.

npm run dev: Inicia o servidor em modo de desenvolvimento.

npm test: Roda todos os testes com Jest.

npm run test:watch: Roda os testes com Jest em modo watch.

npm run test:coverage: Gera o relatório de cobertura dos testes.

npm run cypress:open: Abre a UI do Cypress para testes E2E.

npm run cypress:run: Roda os testes E2E em modo headless.

📊 Estrutura do Banco de Dados

Tabela: autores

id (SERIAL PRIMARY KEY)

nome (VARCHAR(255) NOT NULL)

nacionalidade (VARCHAR(100))

data_nascimento (DATE)

biografia (TEXT)

created_at (TIMESTAMP)

updated_at (TIMESTAMP)

Tabela: livros

id (SERIAL PRIMARY KEY)

titulo (VARCHAR(255) NOT NULL)

isbn (VARCHAR(20) UNIQUE)

ano_publicacao (INTEGER)

genero (VARCHAR(100))

numero_paginas (INTEGER)

autor_id (INTEGER REFERENCES autores(id))

created_at (TIMESTAMP)

updated_at (TIMESTAMP)

🎨 Interface

A interface foi desenvolvida com Bootstrap 5, garantindo um layout limpo, moderno e responsivo. Os principais recursos visuais incluem:

Formulários de cadastro com validação de campos.

Alertas de feedback para o usuário (mensagens de sucesso e erro).

Navegação simples e intuitiva.

Compatibilidade com dispositivos móveis e desktops.

📝 Observações

A arquitetura segue estritamente o padrão Model-View-Controller (MVC).

A segurança contra SQL Injection é garantida pelo uso de prepared statements.

Há validação de dados tanto no frontend (cliente) quanto no backend (servidor).

A aplicação implementa um sistema consistente de tratamento de erros.

O código segue as boas práticas recomendadas para o ecossistema Node.js.

👥 Autor

Projeto: Desenvolvido para a disciplina TAD0203 - Gestão da Qualidade de Software.

Curso: Análise e Desenvolvimento de Sistemas.

Docente: Joel Santos.

Aluno: Matheus dos Santos Bezerra da Silva
