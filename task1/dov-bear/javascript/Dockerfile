FROM node:20-alpine

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci --omit=dev

COPY main.js ./
COPY public ./public
COPY views ./views

ENV PORT=3000
EXPOSE ${PORT}

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
  CMD wget -q --spider http://localhost:${PORT}/healthz || exit 1

ENTRYPOINT ["node", "main.js"]