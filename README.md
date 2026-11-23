Servidor Mumble en AWS EC2

1. Descripción del proyecto

El presente proyecto consiste en la implementación y configuración de un servidor de comunicación por voz utilizando Mumble, una aplicación de código abierto que permite la comunicación de audio en tiempo real entre diferentes usuarios.

El servidor fue desplegado en una instancia de Amazon Web Services (AWS) EC2, utilizando AlmaLinux como sistema operativo y Podman para la administración de contenedores.

El objetivo es contar con un servicio de comunicación accesible mediante una dirección IP pública, permitiendo que diferentes usuarios puedan conectarse desde sus equipos.

2. Objetivos del proyecto

* Implementar un servidor Mumble en la nube.
* Configurar un entorno Linux para administrar el servicio.
* Utilizar Podman para ejecutar el servidor mediante contenedores.
* Habilitar la comunicación mediante los protocolos TCP y UDP.
* Configurar el almacenamiento persistente de información.
* Verificar la disponibilidad y conectividad del servicio.
* Documentar la implementación y las pruebas realizadas.

3. Tecnologías utilizadas

Tecnología	Función
Amazon Web Services (AWS)	Plataforma de infraestructura en la nube
Amazon EC2	Instancia virtual donde se ejecuta el servidor
AlmaLinux	Sistema operativo del servidor
Podman	Administración y ejecución de contenedores
Mumble Server	Servicio de comunicación por voz
GitHub	Almacenamiento y documentación del proyecto

4. Arquitectura del servidor

El servicio se encuentra desplegado dentro de una instancia EC2. En ella se ejecuta AlmaLinux, que permite administrar los recursos del sistema y ejecutar Podman.

Podman ejecuta el contenedor basado en la imagen oficial de Mumble Server. El contenedor utiliza el puerto 64738 para permitir la comunicación de los clientes.

La arquitectura general es:

Usuario → Internet → AWS EC2 → AlmaLinux → Podman → Contenedor Mumble Server.

5. Configuración e implementación

Para implementar el servidor se realizaron las siguientes actividades:

1. Creación de una instancia virtual EC2 en AWS.
2. Configuración del acceso remoto mediante SSH.
3. Preparación del sistema operativo AlmaLinux.
4. Instalación y configuración de Podman.
5. Descarga de la imagen de Mumble Server.
6. Creación y ejecución del contenedor.
7. Configuración de los puertos de comunicación.
8. Verificación del estado del contenedor.
9. Configuración del almacenamiento persistente.
10. Documentación del proyecto en GitHub.

Ejecución del contenedor

El servidor se ejecutó utilizando el siguiente comando:

podman run -d --name mumble \
-p 64738:64738/tcp \
-p 64738:64738/udp \
docker.io/mumblevoip/mumble-server

Este comando crea un contenedor llamado mumble, descarga la imagen si es necesario y publica los puertos correspondientes para permitir las conexiones.

6. Configuración de red

El servidor utiliza el puerto 64738 para recibir las conexiones de los clientes.

Puerto	Protocolo	Función
64738	TCP	Comunicación del servicio
64738	UDP	Comunicación de voz

Además, se requiere permitir el tráfico correspondiente en las reglas de seguridad de AWS para que los usuarios puedan conectarse desde Internet.

7. Persistencia de datos

Se utiliza un volumen de Podman para almacenar información del servidor fuera del sistema de archivos interno del contenedor.

Entre los archivos almacenados se encuentra la base de datos SQLite del servicio.

Esto permite conservar información aunque el contenedor sea eliminado o recreado, siempre que se mantenga el volumen asociado.

8. Verificación del funcionamiento

Para comprobar el funcionamiento del servidor se utilizaron comandos de administración de Podman.

Consultar los contenedores:

podman ps -a

Consultar los registros del servidor:

podman logs mumble

Revisar la configuración del contenedor:

podman inspect mumble

Estas verificaciones permiten revisar el estado del contenedor, los registros del servicio y la configuración de ejecución.

9. Seguridad

Para proteger el entorno se consideraron los siguientes aspectos:

* Acceso administrativo mediante SSH.
* Configuración de reglas de seguridad en AWS.
* Exposición únicamente de los puertos necesarios para el servicio.
* Uso de un contenedor sin modo privilegiado.
* Protección de archivos privados y credenciales.
* Separación de los datos persistentes mediante volúmenes.

10. Problemas encontrados y soluciones

Durante el desarrollo se realizaron diferentes verificaciones para identificar posibles problemas en el funcionamiento del servicio.

Se revisaron los registros del contenedor mediante podman logs, el estado del servicio mediante podman ps -a y la configuración mediante podman inspect.

Estas herramientas permitieron identificar el estado del servidor y analizar posibles problemas de conectividad y ejecución.

11. Conclusiones

La implementación permitió desplegar un servidor Mumble en una infraestructura de nube utilizando AWS EC2, AlmaLinux y Podman.

Se comprobó la ejecución del contenedor y la configuración de los puertos TCP y UDP necesarios para la comunicación.

Asimismo, el uso de volúmenes permitió mantener los datos del servicio fuera del contenedor, mientras que GitHub facilitó la documentación y el almacenamiento del proyecto.

Finalmente, el desarrollo permitió aplicar conocimientos de administración de sistemas operativos, redes, contenedores y servicios en la nube.