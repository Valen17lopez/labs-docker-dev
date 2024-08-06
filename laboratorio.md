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