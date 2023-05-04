FROM node:16 AS builder

WORKDIR /usr/src/app

COPY . .

RUN npm install --omit=dev

FROM gcr.io/distroless/nodejs:16

COPY --from=builder /usr/src/app /app

WORKDIR /app

EXPOSE 3000

CMD [ "app.js" ]