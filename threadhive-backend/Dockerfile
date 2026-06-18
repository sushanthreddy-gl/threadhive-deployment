FROM node:22-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm install --omit=dev

FROM node:22-alpine
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .
# .env is intentionally excluded — inject env vars at runtime via --env-file or -e flags
EXPOSE 8080
ENV PORT=8080
CMD ["node", "main.js"]
