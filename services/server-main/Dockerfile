FROM node:18-alpine

WORKDIR /app

COPY services/server-main/package* ./

RUN npm ci || npm install --production

COPY services/server-main/. .

COPY ./protos ./protos

ENV HOST=0.0.0.0
ENV PORT=5009

EXPOSE 5009

CMD ["node", "index.js"]
