# FROM Imagen:version
FROM node:12 

#copiar  los archivos, a la ruta del contenedor
COPY ["package.json","package-lock.json","/usr/src/"]

# entrar al directorio
WORKDIR /usr/src

#instalar dependencias
RUN npm install

COPY [".","/usr/src/"]

#exponer el puerto
EXPOSE 3000

#ejecutar el proceso 
#CMD ["npx","nodemon", "index.js"]

CMD ["node", "index.js"]
