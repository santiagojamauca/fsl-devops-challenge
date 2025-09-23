# Etapa de build
FROM node:18 AS builder

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Etapa de producción
FROM node:18-alpine

WORKDIR /app
COPY --from=builder /app ./
ENV NODE_ENV=production
CMD ["npm", "start"]
