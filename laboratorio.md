@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
efc2b5ad9eec: Pull complete 
8fe9a55eb80f: Pull complete 
045037a63be8: Pull complete 
7111b42b4bfa: Pull complete 
3dfc528a4df9: Pull complete 
9e891cdb453b: Pull complete 
0f11e17345c5: Pull complete 
Digest: sha256:6af79ae5de407283dcea8b00d5c37ace95441fd58a8b1d2aa1ed93f5511bb18c
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker pull python:3.9
3.9: Pulling from library/python
ca4e5d672725: Pull complete 
30b93c12a9c9: Pull complete 
10d643a5fa82: Pull complete 
d6dc1019d793: Pull complete 
c7d45ab0573c: Pull complete 
564d1c451ea7: Pull complete 
ddfb50ba1977: Pull complete 
91b87d81d4c8: Pull complete 
Digest: sha256:65438c2e26dbf9f5db4b5553e332747fa20722c1b7c7ccc6f8480396ff4186db
Status: Downloaded newer image for python:3.9
docker.io/library/python:3.9

@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker run -it ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
root@5d1797b69ce9:/# 

@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                       PORTS                                   NAMES
e50198bffbc4   httpd     "httpd-foreground"       6 minutes ago    Up 6 minutes                 0.0.0.0:8000->80/tcp, :::8000->80/tcp   priceless_brahmagupta
e0edb38776d2   nginx     "/docker-entrypoint.…"   7 minutes ago    Created                                                              wonderful_clarke
5d1797b69ce9   ubuntu    "bash"                   11 minutes ago   Exited (130) 8 minutes ago                                           hardcore_montalcini
ede7d864b684   nginx     "/docker-entrypoint.…"   12 minutes ago   Created                                                              relaxed_dhawan
b5e5c7b3c07d   nginx     "/docker-entrypoint.…"   12 minutes ago   Up 12 minutes                0.0.0.0:8080->80/tcp, :::8080->80/tcp   unruffled_murdock
@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker rm 5d1797b69ce9
5d1797b69ce9
@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
e0edb38776d21533f89e9f444686f65aec7228a1b0ffe0dd876fa4dff999eadd
ede7d864b68446351da8d26fafc446f29bd949fc6e96a7aa8b1f09f5e4f3fb3c

Total reclaimed space: 0B


## Ejercicio 1: Crear un Dockerfile simple con Ubuntu y actualizar paquetes ##
@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 13.0s (7/7) FINISHED                  docker:default
 => [internal] load build definition from Dockerfile         0.2s
 => => transferring dockerfile: 97B                          0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.7s
 => [auth] library/ubuntu:pull token for registry-1.docker.  0.0s
 => [internal] load .dockerignore                            0.1s
 => => transferring context: 2B                              0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest@sha256:2e863  2.1s
 => => resolve docker.io/library/ubuntu:latest@sha256:2e863  0.1s
 => => sha256:2e863c44b718727c860746568e1d5 1.13kB / 1.13kB  0.0s
 => => sha256:c920ba4cfca05503764b785c16b76d43c 424B / 424B  0.0s
 => => sha256:35a88802559dd2077e584394471dd 2.30kB / 2.30kB  0.0s
 => => sha256:9c704ecd0c694c4cbdd85e589ac 29.71MB / 29.71MB  0.5s
 => => extracting sha256:9c704ecd0c694c4cbdd85e589ac8d1fc3f  1.1s
 => [2/2] RUN apt-get update && apt-get upgrade -y           8.1s
 => exporting to image                                       1.3s
 => => exporting layers                                      1.1s
 => => writing image sha256:68e1714c4bd4df246904012815fe860  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest 


## Ejercicio 2: Construir la imagen del ejercicio 1 ##

@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 8.4s (4/5)                            docker:default
[+] Building 12.2s (5/6)                           docker:default
 => [internal] load build definition from Dockerfile         0.1s
[+] Building 13.0s (6/6) FINISHED                  docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 139B                         0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.2s
 => [internal] load .dockerignore                            0.1s
 => => transferring context: 2B                              0.0s
 => CACHED [1/2] FROM docker.io/library/ubuntu:latest@sha25  0.0s 
 => [2/2] RUN apt-get update && apt-get install -y nginx    11.8s 
 => exporting to image                                       0.5s 
 => => exporting layers                                      0.4s 
 => => writing image sha256:5a24e96ddf0cea277e5147401f57af4  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     0.0s
@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 0.6s (6/6) FINISHED                   docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 139B                         0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.2s
 => [internal] load .dockerignore                            0.1s
 => => transferring context: 2B                              0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest@sha256:2e863  0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y n  0.0s
 => exporting to image                                       0.1s
 => => exporting layers                                      0.0s
 => => writing image sha256:5a24e96ddf0cea277e5147401f57af4  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     0.0s
@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 0.7s (6/6) FINISHED                   docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 139B                         0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.2s
 => [internal] load .dockerignore                            0.1s
 => => transferring context: 2B                              0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest@sha256:2e863  0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y n  0.0s
 => exporting to image                                       0.1s
 => => exporting layers                                      0.0s
 => => writing image sha256:5a24e96ddf0cea277e5147401f57af4  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     0.0s
@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 0.7s (6/6) FINISHED                   docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 139B                         0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.2s
 => [internal] load .dockerignore                            0.1s
 => => transferring context: 2B                              0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest@sha256:2e863  0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y n  0.0s
 => exporting to image                                       0.1s
 => => exporting layers                                      0.0s
 => => writing image sha256:5a24e96ddf0cea277e5147401f57af4  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     0.0s

 ## Ejercicio 3: Crear un Dockerfile para instalar Nginx en Ubuntu ##
 @Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 0.6s (6/6) FINISHED                   docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 138B                         0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.2s
 => [internal] load .dockerignore                            0.1s
 => => transferring context: 2B                              0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest@sha256:2e863  0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y n  0.0s
 => exporting to image                                       0.1s
 => => exporting layers                                      0.0s
 => => writing image sha256:5a24e96ddf0cea277e5147401f57af4  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     0.0s


## Ejercicio 4: Construir y ejecutar la imagen de Nginx

@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 0.7s (7/7) FINISHED                   docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 138B                         0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.2s
 => [auth] library/ubuntu:pull token for registry-1.docker.  0.0s
 => [internal] load .dockerignore                            0.0s
 => => transferring context: 2B                              0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest@sha256:2e863  0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y n  0.0s
 => exporting to image                                       0.1s
 => => exporting layers                                      0.0s
 => => writing image sha256:5a24e96ddf0cea277e5147401f57af4  0.0s
 => => naming to docker.io/library/my-nginx:latest           0.0s
@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker run -d -p 80:80 my-nginx:latest
81c3528aa06d5ea67e0ec2ee93e99e3683470bc499a4eb0f53b64ddde6eeea57


## Ejercicio 5: Modificar el Dockerfile de Nginx para exponer el puerto 80
@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 0.8s (6/6) FINISHED                   docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 148B                         0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.2s
 => [internal] load .dockerignore                            0.1s
 => => transferring context: 2B                              0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest@sha256:2e863  0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y n  0.0s
 => exporting to image                                       0.1s
 => => exporting layers                                      0.0s
 => => writing image sha256:b652852e3989e4efa74b3072fb5010e  0.0s
 => => naming to docker.io/library/my-nginx:latest   


## Ejercicio 1: Copiar un archivo HTML local a una imagen de Nginx

@Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 7.7s (8/8) FINISHED                   docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 94B                          0.0s
 => [internal] load metadata for docker.io/library/nginx:la  0.6s
 => [auth] library/nginx:pull token for registry-1.docker.i  0.0s
 => [internal] load .dockerignore                            0.0s
 => => transferring context: 2B                              0.0s
 => [internal] load build context                            0.3s
 => => transferring context: 31B                             0.0s
 => [1/2] FROM docker.io/library/nginx:latest@sha256:6af79a  5.8s
 => => resolve docker.io/library/nginx:latest@sha256:6af79a  0.2s
 => => sha256:6af79ae5de407283dcea8b00d5c 10.27kB / 10.27kB  0.0s
 => => sha256:baa881b012a49e3c2cd6ab9d80f9f 2.29kB / 2.29kB  0.0s
 => => sha256:a72860cb95fd59e9c696c66441c64 7.30kB / 7.30kB  0.0s
 => => sha256:efc2b5ad9eec05befa54239d53f 29.13MB / 29.13MB  0.5s
 => => sha256:045037a63be803c1d446a5239439580a4 627B / 627B  0.2s
 => => sha256:8fe9a55eb80f3167f7b3a9c39f9 41.83MB / 41.83MB  0.8s
 => => sha256:7111b42b4bfa1b5273abcc4b138983f48 955B / 955B  0.3s
 => => sha256:3dfc528a4df9e1be9b2817271a35cef87 394B / 394B  0.5s
 => => extracting sha256:efc2b5ad9eec05befa54239d53feeae356  1.3s
 => => sha256:0f11e17345c583a30e9cc89b80b14 1.40kB / 1.40kB  0.8s
 => => sha256:9e891cdb453be97c53e1ddbe4b955 1.21kB / 1.21kB  0.9s
 => => extracting sha256:8fe9a55eb80f3167f7b3a9c39f90b9eacf  0.9s
 => => extracting sha256:045037a63be803c1d446a5239439580a49  0.0s
 => => extracting sha256:7111b42b4bfa1b5273abcc4b138983f48f  0.0s
 => => extracting sha256:3dfc528a4df9e1be9b2817271a35cef87f  0.0s
 => => extracting sha256:9e891cdb453be97c53e1ddbe4b955ee710  0.0s
 => => extracting sha256:0f11e17345c583a30e9cc89b80b1423b7b  0.0s
 => [2/2] COPY index.html /usr/share/nginx/html/             0.2s
 => exporting to image                                       0.7s
 => => exporting layers                                      0.6s
 => => writing image sha256:42471ef34f250b2b8dd5baa18976e28  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     0.0s


 ## Ejercicio 2: Usar WORKDIR y copiar un archivo
 @Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 1.9s (9/9) FINISHED                   docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 87B                          0.0s
 => [internal] load metadata for docker.io/library/ubuntu:l  0.2s
 => [auth] library/ubuntu:pull token for registry-1.docker.  0.0s
 => [internal] load .dockerignore                            0.1s
 => => transferring context: 2B                              0.0s
 => CACHED [1/3] FROM docker.io/library/ubuntu:latest@sha25  0.0s
 => [internal] load build context                            0.1s
 => => transferring context: 31B                             0.0s
 => [2/3] WORKDIR /app                                       0.2s
 => [3/3] COPY myfile.txt .                                  0.3s
 => exporting to image                                       0.7s
 => => exporting layers                                      0.6s
 => => writing image sha256:c2eef8758e02b78c236e4c75fee0d27  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     0.0s


 ## Ejercicio 3: Ejecutar un script Python al iniciar el contenedor

 @Valen17lopez ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 26.1s (9/9) FINISHED                  docker:default
 => [internal] load build definition from Dockerfile         0.1s
 => => transferring dockerfile: 111B                         0.0s
 => [internal] load metadata for docker.io/library/python:3  0.6s
 => [auth] library/python:pull token for registry-1.docker.  0.0s
 => [internal] load .dockerignore                            0.0s
 => => transferring context: 2B                              0.0s
 => [1/3] FROM docker.io/library/python:3.9@sha256:65438c2  22.3s
 => => resolve docker.io/library/python:3.9@sha256:65438c2e  0.1s
 => => sha256:9972540d93856f9ca3eff2cf803ff 2.52kB / 2.52kB  0.0s
 => => sha256:83a59ab1a4811d0d1b135849e5071 7.31kB / 7.31kB  0.0s
 => => sha256:ca4e5d6727252f0dbc207fbf283 49.55MB / 49.55MB  0.8s
 => => sha256:65438c2e26dbf9f5db4b5553e33 10.35kB / 10.35kB  0.0s
 => => sha256:30b93c12a9c9326732b35d9e3eb 24.05MB / 24.05MB  0.5s
 => => sha256:10d643a5fa823cd013a108b2076 64.14MB / 64.14MB  1.2s
 => => extracting sha256:ca4e5d6727252f0dbc207fbf283cb95e27  2.4s
 => => sha256:d6dc1019d7935fe82827434da 211.24MB / 211.24MB  4.1s
 => => sha256:c7d45ab0573c09f3315112fe3e8d2 6.16MB / 6.16MB  1.3s
 => => sha256:564d1c451ea70670b349d1250f5 15.82MB / 15.82MB  1.5s
 => => sha256:ddfb50ba1977e47749619886799b60da9 233B / 233B  1.6s
 => => sha256:91b87d81d4c8d2b201b71e0a5b07f 2.70MB / 2.70MB  1.7s
 => => extracting sha256:30b93c12a9c9326732b35d9e3ebe57148a  0.6s
 => => extracting sha256:10d643a5fa823cd013a108b2076f4d2edf  2.5s
 => => extracting sha256:d6dc1019d7935fe82827434da11bf96cf1  6.8s
 => => extracting sha256:c7d45ab0573c09f3315112fe3e8d273f4b  0.3s
 => => extracting sha256:564d1c451ea70670b349d1250f5c057741  0.6s
 => => extracting sha256:ddfb50ba1977e47749619886799b60da9f  0.0s
 => => extracting sha256:91b87d81d4c8d2b201b71e0a5b07fe01ea  0.3s
 => [internal] load build context                            0.1s
 => => transferring context: 30B                             0.0s
 => [2/3] WORKDIR /app                                       0.2s
 => [3/3] COPY script.py .                                   0.2s
 => exporting to image                                       2.2s
 => => exporting layers                                      2.1s
 => => writing image sha256:38ffac2c50d72c15d4adb145753a853  0.0s
 => => naming to docker.io/library/ubuntu-updated:latest     0.0s