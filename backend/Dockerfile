FROM node:20-alpine

WORKDIR /app

RUN apk add --no-cache git

COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY . .

EXPOSE 8080
CMD ["node", "whaticketplus/server.js"]
