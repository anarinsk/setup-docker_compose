## Misson 

- docker pull과 함께 필요한 이미지 내에서 필요한 작업을 수행한다. 
- 

## Testflight 

- `5600H/docker-anari-jupyter-custom.yml`

## How to 

1. Jupyter 이미지를 기반으로 새로 빌드한다. 
2. 기존 yml과 거의 동일하며 build 옵션과 build 파일만 넣어주면 된다. 
3. 실행 명령 예제는 아래와 같다. 
4. docker 컨테이너 안에서 sudo 쓰는 법. `USER root` 옵션을 도커 파일에 넣어준다. 

```shell
> sudo docker-compose -f /mnt/c/Users/anari/github/setup-docker_compose/5600H/docker-anari-jupyter-custom.yml -p jupyter-kor_ up -d
```

## References 

- https://www.44bits.io/ko/post/almost-perfect-development-environment-with-docker-and-docker-compose

