FROM node:18-alpine

WORKDIR /app

COPY services/moods-service/package* ./

RUN npm ci || npm install --production

COPY services/moods-service/. .

COPY ./protos ./protos

ENV HOST=0.0.0.0
ENV PORT=50052

EXPOSE 50052

CMD ["node", "index.js"]
