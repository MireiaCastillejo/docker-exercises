# Ejercicio 5 
   
 ##  Dado el escaso margen para montar la demostración, la opción más ágil y rápida es utilizar una solución basada en contenedores donde levantaréis el motor de indexación (ElasticSearch) y la herramienta de visualización (Kibana)

1. Rellenamos el docker-compose.yml
	```
	version: '3.6'
	services:
	  elasticsearch:
	    #Utilizar la imagen de elasticsearch v7.9.3
	    image: docker.elastic.co/elasticsearch/elasticsearch:7.9.3
	    # Asignar un nombre al contenedor
	    container_name: elasticsearch
	    # Define las siguientes variables de entorno: 
	    # discovery.type=single-node
	    environment:
	      - discovery.type=single-node
	    # Emplazar el contenedor a la red de elastic
	    networks:
	      - elastic
	    # Mapea el Puerto externo 9200 al puerto interno del contenedor 9200
	    # Idem para el puerto 9300
	    ports:
	      - 9200:9200
	      - 9300:9300
	  kibana:
	    # Utilizar la imagen kibana v7.9.3
	    image: docker.elastic.co/kibana/kibana:7.9.3
	    # Asignar un nombre al contenedor
	    container_name: kibana
	    # Emplazar el contenedor a la red de elastic
	    networks:
	      - elastic
	    # Define las siguientes variables de entorno: 
	    # ELASTICSEARCH_HOST=elasticsearch
	    # ELASTICSEARCH_PORT=9200
	    environment:
	      ELASTICSEARCH_HOST: elasticsearch
	      ELASTICSEARCH_PORT: 9200
	    # Mapear el puerto externo 5601 al puerto interno 5601
	    ports:
	    - 5601:5601
	    # El contenedor Kibana depe esperar a la disponibilidad del servicio elasticsearch
	    depends_on:
	     - elasticsearch
	 # Definir la red elastic (bridge)
	networks:
	  elastic:
	    driver: bridge
	```
2. Ejecutamos el comando `docker-compose up que inicia y ejecuta los contenedores
	```
	docker-compose up 
	```
	
![imagen](https://user-images.githubusercontent.com/26769446/141647738-1d8efbc3-fccf-481d-a22b-17941fcdc05e.png)	
![imagen](https://user-images.githubusercontent.com/26769446/141647822-460f0f42-5806-4f02-be07-0dddec1cf41a.png)


	
