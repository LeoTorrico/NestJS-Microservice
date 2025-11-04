FROM node:24 AS builder

WORKDIR /usr/src/app

COPY ./task-service/package*.json ./
RUN npm install

COPY ./task-service .
COPY ./proto ./proto

RUN npm run build

FROM node:24-alpine

WORKDIR /usr/src/app
COPY --from=builder /usr/src/app ./

CMD ["npm", "run", "start:prod"]
