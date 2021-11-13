# Ejercicio 2 
   
 ##  Indica la diferencia entre el uso de la instrucción ADD y COPY (Dockerfile)

`COPY` copia los archivos nuevos de src y los agrega al sistema de archivos del contenedor en la ruta destino. 
 Solo le permite copiar en un directorio local o desde su host (la máquina que crea la imagen de Docker) en la propia imagen de Docker

`ADD` admite otras 2 fuentes:
  -  Primero, puede usar una URL en lugar de un archivo / directorio local es decir permite que <src>sea una URL. 
  -  En segundo lugar, si contiene un archivo tar local en un formato de comprension que reconoce(gzip, bzip2 y xz) se desempaqueta como un directorio.
