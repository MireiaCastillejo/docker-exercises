# Ejercicio 4
   
 ###  Crea una imagen docker a partir de un Dockerfile. Esta aplicación expondrá un servicio en el puerto 8080 y se deberá hacer uso de la instrucción HEALTHCHECK para comprobar si la aplicación está ofreciendo el servicio o por si el contrario existe un problema.
	El healthcheck deberá parametrizarse con la siguiente configuración:
	- La prueba se realizará cada 45 segundos
	- Por cada prueba realizada, se esperará que la aplicación responda en menos de 5 segundos. Si tras 5 segundos no se obtiene respuesta, se
		considera que la prueba habrá fallado
	- Ajustar el tiempo de espera de la primera prueba (Ejemplo: Si la aplicación del contenedor tarda en iniciarse 10s, configurar el parámetro a 15s)
	- El número de reintentos será 2. Si fallan dos pruebas consecutivas, el contenedor deberá cambiar al estado “unhealthy”) 

1. Creamos el Dockerfile 
      ```
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
      ```

2. Creamos la imagen a partir del Dockerfile 
    ```
   ºdocker build -t go-healthcheck
    ```
4. Creamos el contenedor que apunta al puerto 8080
    ```
    docker run -d go-healthcheck 
    ```
