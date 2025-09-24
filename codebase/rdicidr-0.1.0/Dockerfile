# Etapa de build
FROM node:15 AS builder

WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

# Etapa de producción
FROM node:15-alpine

WORKDIR /app
COPY --from=builder /app ./
ENV NODE_ENV=production
CMD ["npm", "start"]
