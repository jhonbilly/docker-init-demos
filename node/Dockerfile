# syntax=docker/dockerfile:1

ARG NODE_VERSION=21.6.2
FROM node:${NODE_VERSION}-alpine

ENV NODE_ENV=production

WORKDIR /usr/src/app

# Copiar archivos de dependencias
COPY package.json .
COPY package-lock.json .

# Instalar dependencias de producción
RUN npm ci --omit=dev

# Cambiar al usuario no root por seguridad
USER node

# Copiar el resto de la aplicación
COPY . .

# Exponer el puerto usado por la app
EXPOSE 8080

# Comando por defecto para ejecutar la app
CMD ["node", "app.js"]
