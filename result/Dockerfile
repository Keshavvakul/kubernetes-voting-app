FROM node:18-slim
# add curl for healthcheck
RUN apt-get update && /
    apt-get install -y --no-install-recommends curl tini

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

ENV PORT=80
EXPOSE 80

CMD ["ls"]

CMD ["node", "server.js"]
