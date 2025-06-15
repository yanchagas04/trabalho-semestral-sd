# Usa imagem oficial do Node
FROM node:18

# Cria diretório de trabalho
WORKDIR /app

# Copia os arquivos de dependência
COPY package*.json ./

# Instala TODAS as dependências (inclusive dev)
RUN npm install

# Copia o restante do código
COPY . .

# Expõe a porta da aplicação
EXPOSE 3001

# Comando para rodar em modo dev com migrate
CMD ["sh", "-c", "npx prisma migrate deploy && npx ts-node-dev --respawn --transpile-only src/server.ts"]
