# setup-docker_compose
cases for my docker-compose 

실제 활용중인 도커 case file을 보관하고 주석을 달아 둔다. 

- 활용하는 PC 마다 디렉토리가 다르기 때문에 이는 디렉토리로 구별한다. 

## Files Added 

### `docker-anari-ds.yml`

- `jupyter/datascience-notebook` 컨테이너와 `rocker/verse` 컨테이너를 구동하기 위한 yml 파일 

### `docker-anari-jupyter.yml`

- `jupyter/datascience-notebook` 컨테이너 구동을 위한 yml 파일 

### `docker-anari-tfgpu.yml`

- CUDA 지원 tf + Jupyter 

## How to build 

+ image를 그대로 가져오는 방식에서 build를 거치는 방식으로 바꾸었다. 
+ 이유 
  + 빌드를 그대로 가져올 경우 빠르긴 하지만 필수적인 커스터마이즈를 거쳐야 한다. 예를 들어 Jupyter의 한글 설치 등등 
  + build 자체를 완성된 image에서 수행하기 때문에 시간상의 손실은 별로 없다. 
  + 오히려 Ubuntu update & upgrade를 수행할 수 있는 장점이 있다. 
  + `image`를 `build`로 바꾸는 것 이외에 나머지는 별로 할 게 없다. 

### 변경된 부분 

+ 각각의 하드웨어 환경에 맞춰 변경 하면 된다. 먼저 세팅된 것은 `5600H`
  + yml 파일 수정 
  + 각 디렉토리 아래 하위 디렉토리로 `dockerfiles` 디렉토리를 두었다. 여기 docker 빌드를 위한 정보가 담긴다. 

## Custom Parts 

- 환경 비밀 번호 

```shell
## For Jupyter 
environment:
            - GRANT_SUDO=yes 
            - JUPYTER_ENABLE_LAB=yes
            - JUPYTER_TOKEN=1022
```

```shell
## For Rocker 
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
 - `-p`: compose에서 쓰는 이름. 네트워크도 이때 같이 묶이는 것 같다... (미확인)
 - `up`: 모든 콘테이너를 한번에 올리자! 
