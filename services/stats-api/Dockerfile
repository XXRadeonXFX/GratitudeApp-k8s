FROM node:18-alpine

WORKDIR /app

COPY services/stats-api/package* ./

RUN npm ci || npm install --production

COPY services/stats-api/. .

COPY ./protos ./protos

ENV HOST=0.0.0.0
ENV PORT=5003

EXPOSE 5003

CMD ["node", "index.js"]
