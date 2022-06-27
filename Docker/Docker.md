# Docker 

Es una plataforma que permite construir, ejecutar y compartir aplicaciones mediante contenedores.

https://github.com/platzi/docker

## Play with docker 
Permite ejecutar comando de Docker en una terminal linux, con un tiempo limitado 3hrs 

# Contenedor

## Comandos Básicos:

Crear contenedor 

    docker run --name nombre@imagen

Correr contenedor

    docker run -it imagen

    docker run --name nombre -d imagen comando 

        Ej. docker run --name alwaysrun -d ubuntu tail -f /dev/null

Ejecutar algun comnado en un contenedor

    docker exec -it nombre/id comando

Renombrar contenedor 

    docker rename nombre nuevoNombre

Ver contenedores corriendo

    docker ps 

Ver todos los contenedores:

    docker ps -a

Ver toda la  información del contenedor:

    docker inspect id/name

Detener un contenedor:

    docker stop nombre/id

Eliminar contenedor:

    docker rm nombre/id

Eliminar el contenedor al detenerse: 

    docker run -rm imagen

Eliminar todos los contenedores que no se estan ejecutando:

    docker container prune

Eliminar todos los contenedores

    docker rm -f $(docker ps -aq)

Eliminar todo el conjunto de volumenes, contenedores, red

    docker system prune


## Exponiendo Contenedores

    docker run --name nombre -p puertoLocal:puertoContenedor imagen

Segundo plano: 
        docker run --name nombre -d -p puertoLocal:puertoContenedor imagen


Ver logs del contenedor: 

    - docker logs nombre/id
    - docker logs -f  nombre/id (ver conforme vayan llegando)
    - docker logs --tail numero -f  nombre/id (limitar cantidad)


## Bind mounts

    docker run -d --name db -v  rutaLocal:rutaContenedor imagen

## Volúmenes (Es mas seguro)

Ver volumenes creados: 

    docker volume ls

Crear un volumen:

    docker volume create nombre

Montar un volumen: 

    docker run -d --name db --mount src=volumen,dst=rutaContenedor imagen 

## Insertar y extraer archivos de un contenedor 

Valido para archivos y directorios: 

    docker cp rutaOrigen nombreContenedor:rutaContenedor

    docker cp nombrecontenedor:rutaContenedor rutaOrigen

# Imagenes

Listar las imagenes: 

    docker image ls

## Docker hub

Descargar una imagen 

    docker pull nombre:version

Publicar imagen 

    docker login

    docker push usuarioDockerHub/imagen:version

## Contruir una imagen propia 

1. Crear un Dockerfile 
2. Construir la imagen

        docker build -t nombre:version . 

3. Correr un contenedor con la imagen creada

        docker run -it nombre:version

4. Renombrar imagenes

        docker tag nombre:version usurioDockerHub/imagen:version

5. Publicar imagen 

        docker push usuarioDockerHub/imagen:version

## Capas

    docker history imagen:version

Herramienta para explorar las capas de una imagen de docker: 
    https://github.com/wagoodman/dive