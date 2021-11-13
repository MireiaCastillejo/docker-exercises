# Ejercicio 4
   
 ### Crea una imagen docker a partir de un Dockerfile. Esta aplicación expondrá un servicio en el puerto 8080 y se deberá hacer uso de la instrucción HEALTHCHECK para comprobar si la aplicación está ofreciendo el servicio o por si el contrario existe un problema.
	El healthcheck deberá parametrizarse con la siguiente configuración:
	- La prueba se realizará cada 45 segundos
	- Por cada prueba realizada, se esperará que la aplicación responda en menos de 5 segundos. Si tras 5 segundos no se obtiene respuesta, se
		considera que la prueba habrá fallado
	- Ajustar el tiempo de espera de la primera prueba (Ejemplo: Si la aplicación del contenedor tarda en iniciarse 10s, configurar el parámetro a 15s)
	- El número de reintentos será 2. Si fallan dos pruebas consecutivas, el contenedor deberá cambiar al estado “unhealthy”) 

1. Creamos el Dockerfile 
      ```
	FROM nginx:latest
	HEALTHCHECK --interval=45s --timeout=5s --start-period=15s --retries=2 \
  	CMD curl --fail http://localhost || exit 1
	
      ```

2. A partir del Dockerfile hacemos un build 
    ```
   docker build -t go-healthcheck .
    ```
3. Creamos el contenedor que apunta al puerto 8080
    ```
    docker run -d -p 8080:80 go-healthcheck    
    ```
4. Hacemos `docker ps` y esperamos a que el STATUS pase a healthy
<img width="1645" alt="Captura de pantalla 2021-11-13 a las 16 34 48" src="https://user-images.githubusercontent.com/26769446/141649743-9a7029c0-411d-412e-a27e-639d8bc99483.png">
