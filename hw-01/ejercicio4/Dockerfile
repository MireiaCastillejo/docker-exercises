# Use ngnix base image
FROM nginx:1.19.3-alpine

# Copy src files inside app folder
COPY html /usr/share/nginx/html 
RUN apk update && apk add curl

EXPOSE 8080

HEALTHCHECK --interval=45s --timeout=5s --retries=2 CMD curl --fail http://localhost:8080 || exit  1
