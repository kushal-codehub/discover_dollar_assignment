FROM node:18-alpine

WORKDIR /usr/src/app

# copy package.json first for caching
COPY package*.json ./
RUN npm install --only=production

# copy the rest of backend source (relative to build context ./backend)
COPY . .

EXPOSE 8080
ENV NODE_ENV=production
CMD ["node", "server.js"]
