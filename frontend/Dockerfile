# Stage 1: Builder
FROM --platform=$BUILDPLATFORM node:18 AS builder
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: Runtime
FROM --platform=linux/amd64 node:16-alpine
WORKDIR /app
COPY --from=builder /app/build ./build
COPY --from=builder /app/package.json ./
COPY --from=builder /app/node_modules ./node_modules

# Установка http-server глобально (более надежно чем npx)
RUN npm install -g http-server

EXPOSE 8000
CMD ["http-server", "-p", "8000", "/app/build"]