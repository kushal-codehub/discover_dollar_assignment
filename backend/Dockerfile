# backend/Dockerfile
FROM node:18-alpine

WORKDIR /usr/src/app

COPY backend/package*.json ./

RUN npm ci --only=production

# copy source
COPY backend/ .

EXPOSE 8080

ENV NODE_ENV=production

CMD ["node", "server.js"]
