# setup-docker_compose
cases for my docker-compose 

실제 활용중인 도커 case file을 보관하고 주석을 달아 둔다. 

- 활용하는 PC 마다 디렉토리가 다르기 때문에 이는 디렉토리리로 구별한다. 

## Files Added 

### `docker-anari-ds.yml`

- `jupyter/datascience-notebook` 컨테이너와 `rocker/verse` 컨테이너를 구동하기 위한 yml 파일 

### `docker-anari-jupyter.yml`

- `jupyter/datascience-notebook` 컨테이너 구동을 위한 yml 파일 

## Custom Parts 

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

# Docker compose 실행 

- 여러 옵션에 관해서는 아래 참고 
  - https://docs.docker.com/compose/reference/overview/
  
- 표준적인 실행 옵션은 아래와 같다. 

```shell
sudo docker-compose -f /mnt/c/Users/anari/github/setup-docker_compose/5600h/docker-anari-ds.yml -p "anari-ds" up -d
```
 - `-f`: yml file을 쓴다. 
 - `-p`: compose 이름 
 - `up`: 모든 콘테이너를 한번에 올리자! 
