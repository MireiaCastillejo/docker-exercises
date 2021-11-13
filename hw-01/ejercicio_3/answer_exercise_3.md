# Ejercicio 3
   
 ##  Crea un contenedor con las siguientes especificaciones: 
      a.	Utilizar la imagen base NGINX haciendo uso de la versión 1.19.3
      b. Al acceder a la URL localhost:8080/index.html aparecerá el mensaje HOMEWORK 1
      c. Persistir el fichero index.html en un volumen llamado static_content 

1.Creamos un volumen llamado static_content 
      ```
      docker volume create static_content
      ```
2.Creamos el Dockerfile creando una imagen ngninx y copiando la carpeta html (local) a la carpeta de la imagen
      ```
      # Use ngnix base image
      FROM ngnix:1.19.3-alpine

      # Copy src files inside app folder
      COPY html /usr/share/nginx/html 

      ```

3.Creamos la imagen a partir del Dockerfile 
    ```
    docker build -t nginx-demo .
    ```
4. Creamos el contenedor que apunta al puerto 8080
    ```
    docker run -d --name nginx-demo -p 8080:80 -v static_content:/usr/share/nginx/html nginx-demo
    ```