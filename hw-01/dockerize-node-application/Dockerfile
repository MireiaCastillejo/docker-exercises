# Use NodeJS base image
FROM nginx:1.19.3

# Update packages inside container image
# Create folder app
WORKDIR /app

# Copy src files inside app folder
COPY src/package.json ./
COPY src/app.js ./
# COPY src/* .  es lo mismo metiendo tood

# Execute npm install process
RUN npm install


# Expose port 8080
EXPOSE 8080

#Inicial delay seconds
HEALTHCHECK --interval=45s --timeout=5s --retries=2 --start-period=15s CMD curl --fail https://localhost/ || exit 1 (instalar curl en el contenedor)

# Execute npm start
CMD [ "node", "app.js" ]
