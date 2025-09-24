# Stage build
FROM node:15 AS builder

WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

# Stage producción
FROM node:15-alpine

WORKDIR /app
COPY --from=builder /app ./

ENV NODE_ENV=production
ENV PORT=8080

EXPOSE 8080
CMD ["npm", "start"]
