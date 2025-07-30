# 🚀 Nest Clean - Forum API

Uma API REST robusta para um sistema de fórum construída com **NestJS**, seguindo os princípios de **Clean Architecture** e **Domain-Driven Design (DDD)**.

## 📋 Sobre o Projeto

Este projeto implementa um sistema de fórum completo onde usuários podem:
- Criar e gerenciar perguntas
- Responder perguntas de outros usuários
- Comentar em perguntas e respostas
- Sistema de notificações
- Autenticação JWT
- Diferentes níveis de usuário (Estudante/Instrutor)

## 🏗️ Arquitetura

O projeto segue os princípios de **Clean Architecture** com:
- **Domain Layer**: Entidades de negócio, casos de uso e regras de domínio
- **Infrastructure Layer**: Implementações concretas (banco de dados, autenticação)
- **Application Layer**: Controllers e DTOs
- **Core Layer**: Utilitários e abstrações compartilhadas

## 🛠️ Tecnologias Utilizadas

- **[NestJS](https://nestjs.com/)** - Framework Node.js progressivo
- **[Prisma](https://prisma.io/)** - ORM moderno para TypeScript
- **[PostgreSQL](https://postgresql.org/)** - Banco de dados relacional
- **[JWT](https://jwt.io/)** - Autenticação baseada em tokens
- **[Zod](https://zod.dev/)** - Validação de esquemas TypeScript
- **[Vitest](https://vitest.dev/)** - Framework de testes rápido
- **[Docker](https://docker.com/)** - Containerização
- **[bcryptjs](https://github.com/dcodeIO/bcrypt.js)** - Hash de senhas

## 📦 Pré-requisitos

- **Node.js** (versão 18 ou superior)
- **Docker** e **Docker Compose**
- **npm** ou **yarn**

## 🚀 Como Executar

### 1. Clone o repositório
```bash
git clone <url-do-repositorio>
cd nest-clean
```

### 2. Instale as dependências
```bash
npm install
```

### 3. Configure as variáveis de ambiente
```bash
cp .env.example .env
```

Edite o arquivo `.env` com suas configurações:
```env
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/nest-clean?schema=public"
PORT=3333
JWT_PRIVATE_KEY="sua-chave-privada-jwt"
JWT_PUBLIC_KEY="sua-chave-publica-jwt"
```

### 4. Inicie o banco de dados
```bash
docker-compose up -d
```

### 5. Execute as migrações
```bash
npx prisma migrate dev
```

### 6. Inicie a aplicação
```bash
# Desenvolvimento
npm run start:dev

# Produção
npm run build
npm run start:prod
```

A API estará disponível em `http://localhost:3333`

## 🧪 Testes

```bash
# Testes unitários
npm run test

# Testes em modo watch
npm run test:watch

# Testes E2E
npm run test:e2e

# Coverage
npm run test:cov
```

## 📚 Documentação da API

### Autenticação
- `POST /sessions` - Login do usuário
- `POST /accounts` - Criar nova conta

### Perguntas
- `GET /questions` - Listar perguntas
- `POST /questions` - Criar pergunta
- `GET /questions/:id` - Buscar pergunta por ID
- `PUT /questions/:id` - Editar pergunta
- `DELETE /questions/:id` - Deletar pergunta

### Respostas
- `POST /questions/:questionId/answers` - Responder pergunta
- `PUT /answers/:id` - Editar resposta
- `DELETE /answers/:id` - Deletar resposta
- `PATCH /answers/:id/choose-as-best` - Escolher melhor resposta

### Comentários
- `POST /questions/:questionId/comments` - Comentar pergunta
- `POST /answers/:answerId/comments` - Comentar resposta
- `DELETE /questions/comments/:id` - Deletar comentário da pergunta
- `DELETE /answers/comments/:id` - Deletar comentário da resposta

## 🗂️ Estrutura do Projeto

```
src/
├── core/                 # Camada central (Either, entidades base, etc.)
├── domain/              # Camada de domínio
│   ├── forum/          # Contexto do fórum
│   └── notification/   # Contexto de notificações
└── infra/              # Camada de infraestrutura
    ├── auth/           # Autenticação JWT
    ├── database/       # Configuração do Prisma
    └── http/           # Controllers e DTOs
```

## 🔐 Autenticação

A API utiliza **JWT (JSON Web Tokens)** para autenticação. Após o login, inclua o token no header:

```
Authorization: Bearer <seu-token-jwt>
```

## 🐳 Docker

O projeto inclui configuração Docker para o banco PostgreSQL:

```bash
# Iniciar containers
docker-compose up -d

# Parar containers
docker-compose down

# Ver logs
docker-compose logs -f
```

## 📊 Banco de Dados

### Modelos Principais

- **User**: Usuários do sistema (estudantes/instrutores)
- **Question**: Perguntas do fórum
- **Answer**: Respostas às perguntas
- **QuestionComment**: Comentários em perguntas
- **AnswerComment**: Comentários em respostas
- **Notification**: Sistema de notificações

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📝 Scripts Disponíveis

```bash
npm run build          # Build da aplicação
npm run start          # Iniciar aplicação
npm run start:dev      # Iniciar em modo desenvolvimento
npm run start:debug    # Iniciar em modo debug
npm run lint           # Executar linter
npm run format         # Formatar código
npm run test           # Executar testes
npm run test:e2e       # Executar testes E2E
```

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👨‍💻 Autor

**Denis Raineri**

---

⭐ Se este projeto te ajudou, considere dar uma estrela!