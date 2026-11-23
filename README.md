# Servidor Mumble en AWS EC2

## 1. Descripción del proyecto

Implementación de un servidor de comunicación por voz Mumble en una instancia de AWS EC2, utilizando Podman para ejecutar el servicio mediante contenedores.

## 2. Tecnologías utilizadas

- AWS EC2
- AlmaLinux
- Podman
- Mumble Server
- Git y GitHub

## 3. Configuración del servidor

- Puerto TCP: 64738
- Puerto UDP: 64738
- Límite de usuarios: 100
- Volumen persistente para almacenar los datos del servidor.

## 4. Imagen utilizada

docker.io/mumblevoip/mumble-server:latest

## 5. Archivo de configuración

El proyecto incluye el archivo mumble_server_config.ini con los parámetros principales del servidor.

## 6. Conexión

Para conectarse se necesita la dirección pública de la instancia EC2 y el puerto 64738.

Se utiliza un cliente Mumble para establecer la conexión.

## 7. Administración

El contenedor se administra mediante comandos de Podman.

## 8. Seguridad

El contenedor funciona sin utilizar el modo privilegiado (--privileged).
