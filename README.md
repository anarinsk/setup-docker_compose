# setup-docker_compose
cases for my docker-compose 

실제 활용중인 도커 case file을 보관하고 주석을 달아 둔다. 

## `docker-anari-ds.yml`

- `jupyter/datascience-notebook` 컨테이너와 `rocker/verse` 컨테이너를 구동하기 위한 yml 파일 

### Custiom parts 

- 환경 비밀 번호 

```shell
environment:
            - GRANT_SUDO=yes 
            - JUPYTER_ENABLE_LAB=yes
            - JUPYTER_TOKEN=1022
```

```shell
environment: 
            #- DISABLE_AUTH=true
            - PASSWORD=1022
            - ROOT=TRUE 
```

- 볼륨 연결 

```shell
volumes: 
            - /mnt/c/Users/anari/github:/home/jovyan/github-anari
```

```shell
volumes: 
            - /mnt/c/Users/anari/github:/home/rstudio/github-anari
```

- `container_name`은 컨테이너의 이름을 정해준다. 

