# DEVCONTAINERS- DOCKER + GITHUB
---


### ANSWER QUESTIONS LIKE THAT...

1. Why you should use DevContainers for your Geospatial Development...?
2. I decided not to install anything related to python, such as conda, virtualenv or miniconda. 
   Instead, I opted for Git and Docker.

### STEP BY STEP:
1. Install Docker and git


#### PROCESO DE INSALAR EL REPOSITORIO
**Installation, me salieron errores para instalar los sources**
$ sudo apt update\
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
$ sudo apt-key adv --refresh-keys

#### INSTALACION EN UBUNTU
**Despues de corregir:**

1. $ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
2. $ sudo docker run hello-world


### DONE
$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
719385e32844: Pull complete 
Digest: sha256:dcba6daec718f547568c562956fa47e1b03673dd010fe6ee58ca806767031d1c
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
### COMANDOS DOCKER

$ docker run hello-world
To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bas
**To pull it from Docker Hub we can just type the following commands.**

$ docker pull jupyter/datascience-notebook


### RUN JUPYTER WITHIN THE CONATINER ###
Ejecute Jupyter dentro del contenedor
Una vez descargada la imagen, podemos construir un contenedor a partir de ella.
 Hay dos puntos importantes a tener en cuenta:

Reenvío del puerto de escucha: 
cuando ejecutamos el contenedor, debemos vincular el puerto que utilizará Jupyter
 desde la máquina host al contenedor. Esto se puede lograr con el argumento -p, 
así: -p 8888:8888.
 Esto significa que cualquier intento de acceder al puerto host 8888 se reenviará
 al mismo puerto dentro del contenedor.


Vincular una carpeta local: para guardar los cuadernos en la máquina host, debemos vincular una carpeta local a una ruta dentro del contenedor. Esto se puede hacer usando la opción -v. En este caso, dado que la imagen de Jupyter inicia el servidor en /home/jovyan/, vincularemos nuestra carpeta local a este destino usando el siguiente argumento -v d:/Projects:/home/jovyan/projects.

En mi caso en ubuntu esto funciona asi:
Mi carpeta donde quiero almacenar los archivos en mi sistema : /home/soporte/workspace/docker_env/projects
Carpeta donde se generan los nuevos archivos del contenedor: /home/jovyan/work

docker run -it -p 8888:8888 -v /home/soporte/workspace/docker_env/projects:/home/jovyan/work jupyter/datascience-notebook
