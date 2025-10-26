FROM node:18-alpine

WORKDIR /app

COPY services/api-gateway/package* ./


RUN npm ci || npm install --production

COPY services/api-gateway/. .

COPY ./protos ./protos

ENV HOST=0.0.0.0
ENV PORT=5000

EXPOSE 5000

CMD ["node", "index.js"]
