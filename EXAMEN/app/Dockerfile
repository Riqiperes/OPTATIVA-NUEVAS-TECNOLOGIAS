FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
COPY public ./public 
RUN npm install
COPY . .
RUN npm run build

FROM node:20-alpine AS runner
WORKDIR /app
RUN mkdir -p /app/public
COPY --from=builder /app/public ./public
COPY --from=builder /app/.next ./.next
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./package.json
RUN [ -f /app/next.config.js ] || cp /app/next.config.js ./

EXPOSE 80
ENV PORT=80
CMD ["npm", "start"]
