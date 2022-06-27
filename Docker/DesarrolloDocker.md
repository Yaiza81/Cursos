# Desarrollo de aplicaciones con Docker

1. Desarrollo de la aplicacion
2. Añadir Dockerfile, ver ejemplo
3. Construir la imagen 

        docker build -t nombre . 

4. Correr imagen 

        docker run -p 3000:3000 nombre


### Monitorear cambios con node

    docker run -p puerto:puertoContenedor -v  rutaLocal:rutaContenedor imagen

Ejemplo:

    docker run -p 3000:3000 -v /Users/pc/code/docker/index.js:/usr/src/index.js app

### Administrando recursos 

Limitar la memoria

    docker run -d --name nombre --memory 1g imagen

Listar
    
    docker stats


## Colaboración entre contenedores 

Red:
    docker network ls 

    docker network create --attachable name 

    docker network inspect name

Conectar contenedor a la red: 

    docker network connect nombreRed nombreContenedor

### Asignando variable de entorno
Se le agrega el nombre del contenedor y al estar conectado a la red, toma automaticamente la red

    docker run -d --name app -p 3000:3000 --env MONGO_URL=mongodb://db:27017/test app


# Docker Compose

1. Crear archivo docker-compose.yml, ver ejemplo

        docker-compose up -d 

Ver los logs

        docker-compose logs nombre

Ejecutar un comando 

        docker-compose exec nombre comando

Destruir todo lo creado con el docker-compose

        docker-compose down

Construir 

        docker-compose build app 

Si quisieramos tener alguna replica 
* Agregar el rango en puertos 

        docker-compose up -d --scale app=2

# Compose: override

Compose para personalizar en ambientes apartes 

1. Crear un archivo docker-compose.override.yml 

Se combina con el archivo base
* Los puertos es aconsejable solo en uno de los archivos 

# Detener contenedores

### Shell vs EXEC

    docker exec nombre ps -ef

Evitar los comandos fuera de corchetes, los toma como shell

    CMD /loop.sh -> CMD ["/loop.sh"]




