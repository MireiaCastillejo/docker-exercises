FROM node:alpine3.14

RUN apk update --no-cache add curl

WORKDIR /app
COPY src /.
RUN npm install

EXPOSE 8080

HEALTHCHECK --interval=45s \
            --timeout=5s \
            --start-period=15s \
            --retries=2 \
            CMD curl http://localhost:8080 || exit 1

CMD ["npm","start"]