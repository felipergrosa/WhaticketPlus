FROM node:20-alpine AS build

WORKDIR /app
# Instala o git (necessário para dependências git no npm install)
RUN apk add --no-cache git

COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

FROM node:20-alpine
WORKDIR /app
COPY --from=build /app/dist ./dist
COPY --from=build /app/node_modules ./node_modules
COPY package*.json ./
EXPOSE 8080
CMD ["node", "dist/server.js"]
