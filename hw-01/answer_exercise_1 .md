# Ejercicio 1 
   
 ##  Indica la diferencia entre el uso de la instrucción CMD y ENTRYPOINT (Dockerfile)

`CMD`  define comandos predeterminados para un contenedores, pero hay que tener en cuenta que es una instrucción la cual los usuarios pueden anular fácilmente

`ENTRYPOINT` especifica el ejecutable que usará el contenedor, pero este no puede ser reemplazado y todos los parámetros pasados por la línea de comandos serán anexados al comando.

