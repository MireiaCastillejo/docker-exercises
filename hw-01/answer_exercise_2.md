{\rtf1\ansi\ansicpg1252\cocoartf2578
\cocoatextscaling0\cocoaplatform0{\fonttbl}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
}
COPY copia los archivos nuevas de src y los agregará al sistema de archivos del contenedor en la ruta destino. Solo le permite copiar en un directorio local o desde su host (la máquina que crea la imagen de Docker) en la propia imagen de Docker
ADD admite otras 2 fuentes:
 Primero, puede usar una URL en lugar de un archivo / directorio local es decir permite que <src>sea una URL. 
 En segundo lugar, si contiene un archivo tar local en un formato de comprension que reconoce(gzip, bzip2 y xz) se desempaqueta como un directorio.
