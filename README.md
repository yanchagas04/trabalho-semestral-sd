# MelembraAI - Relatório do Sistema

## Discentes
**Vinícius Fernandes de Oliveira**  
[![GitHub](https://img.shields.io/badge/GitHub-vfdeoliveira1-blue?style=flat-square&logo=github)](https://github.com/vfdeoliveira1)

**Vitor Hugo de Jesus Santos**  
[![GitHub](https://img.shields.io/badge/GitHub-vhjsoficial1-blue?style=flat-square&logo=github)](https://github.com/vhjsoficial1)

**Yan Campêlo das Chagas**  
[![GitHub](https://img.shields.io/badge/GitHub-yanchagas04-blue?style=flat-square&logo=github)](https://github.com/yanchagas04) 

Este relatório detalha a arquitetura, funcionalidades e tecnologias utilizadas no sistema **MelembraAI**, um gerenciador de tarefas inteligente. O sistema é dividido em duas partes principais: um **Backend** (API) e um **Frontend** (interface do usuário).

## 1. Arquitetura do Sistema

O MelembraAI adota uma arquitetura cliente-servidor, onde o Frontend atua como cliente, consumindo os serviços e dados fornecidos pela API do Backend. Essa separação permite o desenvolvimento e a implantação independentes de cada componente, facilitando a escalabilidade e a manutenção.

### 1.1. Backend

O Backend é uma API RESTful desenvolvida em Node.js com TypeScript, utilizando o framework Express. Ele é responsável por toda a lógica de negócio, persistência de dados e autenticação de usuários. A comunicação com o banco de dados é realizada através do ORM Prisma.

**Tecnologias Utilizadas no Backend:**

- **Node.js:** Ambiente de execução JavaScript no servidor.
- **Express:** Framework web para construção de APIs RESTful.
- **TypeScript:** Linguagem de programação que adiciona tipagem estática ao JavaScript, melhorando a robustez do código.
- **Prisma:** ORM (Object-Relational Mapper) que facilita a interação com o banco de dados de forma tipada e eficiente.
- **SQLite:** Banco de dados leve utilizado para desenvolvimento.
- **Docker:** Utilizado para conteinerização da aplicação, conforme indicado pelos arquivos `Dockerfile` e `docker-compose.yml`.

**Estrutura de Diretórios do Backend:**

```
Backend/
├── src/
│   ├── config/ (Configurações, como Swagger)
│   ├── controllers/ (Lógica de negócio para as rotas)
│   ├── middlewares/ (Middlewares para processamento de requisições)
│   ├── models/ (Definições de modelos de dados)
│   ├── routes/ (Definição das rotas da API)
│   ├── services/ (Serviços de negócio)
│   └── server.ts (Ponto de entrada da aplicação)
├── prisma/ (Esquemas do Prisma e migrações de banco de dados)
├── Dockerfile
├── docker-compose.yml
├── package.json
├── package-lock.json
├── README.md
└── tsconfig.json
```

### 1.2. Frontend

O Frontend é uma aplicação web desenvolvida com Next.js, um framework React para construção de interfaces de usuário. Ele é responsável por apresentar os dados ao usuário e interagir com a API do Backend para realizar operações.

**Tecnologias Utilizadas no Frontend:**

- **Next.js:** Framework React para construção de aplicações web com renderização do lado do servidor (SSR) e geração de sites estáticos (SSG).
- **React:** Biblioteca JavaScript para construção de interfaces de usuário.
- **TypeScript:** Utilizado para tipagem estática.

**Estrutura de Diretórios do Frontend:**

```
Frontend/
├── src/
│   ├── app/ (Páginas da aplicação)
│   ├── components/ (Componentes reutilizáveis da UI)
│   └── ...
├── public/ (Arquivos estáticos)
├── package.json
├── package-lock.json
├── README.md
├── next.config.ts
├── postcss.config.mjs
├── eslint.config.mjs
└── tsconfig.json
```




## 2. Funcionalidades

O sistema MelembraAI oferece as seguintes funcionalidades principais:

### 2.1. Autenticação de Usuários

Permite que os usuários se registrem e façam login no sistema para acessar suas tarefas. O Backend gerencia a autenticação, enquanto o Frontend fornece as interfaces de registro e login.

### 2.2. Gerenciamento de Tarefas

Os usuários podem criar, visualizar, editar e remover suas tarefas. As tarefas são armazenadas no Backend e exibidas de forma organizada no Frontend. As funcionalidades incluem:

- **Criação de Tarefas:** Adicionar novas tarefas com detalhes como título, descrição, data e hora.
- **Visualização de Tarefas:** Exibir uma lista de tarefas, possivelmente com filtros por data ou status.
- **Edição de Tarefas:** Modificar os detalhes de tarefas existentes.
- **Remoção de Tarefas:** Excluir tarefas do sistema.

### 2.3. Sugestões Inteligentes de Tarefas

Conforme mencionado no `README.md` do Backend, o sistema possui a capacidade de fornecer sugestões inteligentes de tarefas. Embora os detalhes da implementação não estejam explícitos nos arquivos analisados até o momento, essa funcionalidade indica um componente de inteligência ou automação para auxiliar o usuário na organização de suas atividades.

## 3. Componentes Principais

### 3.1. Backend (API RESTful)

- **Rotas de Autenticação (`authRoutes.ts`):** Gerenciam o registro e login de usuários.
- **Rotas de Atividades (`activityRoutes.ts`):** Gerenciam as operações CRUD (Criar, Ler, Atualizar, Deletar) de tarefas.
- **Controladores:** Contêm a lógica de negócio para cada rota, interagindo com os serviços e o banco de dados.
- **Serviços:** Abstraem a lógica de negócio e a interação com o banco de dados.
- **Prisma:** ORM para manipulação do banco de dados (SQLite em desenvolvimento).
- **Swagger:** Ferramenta para documentação e teste da API, acessível via `/docs`.

### 3.2. Frontend (Aplicação Web)

- **Páginas (`src/app/`):** Estrutura as diferentes telas da aplicação, como `AreaLogada`, `MinhaConta`, `TelaLogin`, `TelaRegistro`.
- **Componentes (`src/components/`):** Contém componentes reutilizáveis da interface do usuário, como `MinhaConta`, `Tarefas`, `TelaLogin`, `TelaRegistro`, `BarraLateral`, `SeletorDiaMes`.
- **Context API/Redux (implícito):** Embora não explicitamente detalhado, é provável que o sistema utilize alguma forma de gerenciamento de estado para compartilhar dados entre componentes, dada a complexidade de uma aplicação de gerenciamento de tarefas.




## 4. Conclusão

O sistema MelembraAI é uma aplicação de gerenciamento de tarefas robusta, construída com tecnologias modernas e uma arquitetura bem definida de Backend e Frontend. A separação das responsabilidades entre a API RESTful (Node.js, Express, Prisma) e a interface do usuário (Next.js, React) permite flexibilidade no desenvolvimento, escalabilidade e manutenção.

A inclusão de funcionalidades como autenticação de usuários e gerenciamento completo de tarefas, juntamente com a promessa de 


sugestões inteligentes de tarefas, posiciona o MelembraAI como uma ferramenta promissora para organização pessoal e produtividade.

## 5. Como Executar o Projeto

O processo envolve:

1.  **Iniciar o Backend:** 
- docker compose up ou docker-compose up, que subirá um contêiner docker com o Backend exposto na porta 3001 do localhost
2.  **Configurar o Frontend:**
- Instalar dependências (npm install)
- Definir o arquivo .env com a url do backend (http://localhost:3001)
3. **Iniciar o servidor de desenvolvimento:**
- Rodar npm run dev, deixando o servidor exposto na porta (http://localhost:5173).

O uso de Docker e Docker Compose foi feito para facilitar a configuração do ambiente, indicado pelos arquivos `Dockerfile` e `docker-compose.yml` presentes no diretório `Backend`.


