# Etapa de build
FROM node:20-alpine
WORKDIR /app
COPY package*.json ./
RUN echo "==== Files in /app ====" && ls -la /app
RUN cat package.json
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

# Etapa de produção
FROM node:20-alpine
WORKDIR /app
COPY --from=build /app/dist ./dist
COPY --from=build /app/node_modules ./node_modules
COPY package*.json ./
EXPOSE 8080
CMD ["node", "dist/server.js"]
