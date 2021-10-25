# setup-docker_compose

## What

- podman에 맞게 docker-compose 리스트럭처링을 한다. 

## Why 

- Jupyter 기반 컨테이너의 경우에는 큰 문제 없이 작동한다. 
- Rocker 및 RStudio 기반 컨테이너들은 문제가 많다. 

## How 

- Jupyter 둘을 묶은 yml 파일 `anari-jupyter.yml`
- Rocker 이미지를 별도로 `anari-rocker.yml`

### Classification 

- 디렉토리 구조 
  + 컨테이너를 돌리는 컴퓨터 환경 
    + 5600H: 한성 노트북 
    + Work: 회사 컴퓨터 
- `A_B_C.yml` 구조로 파일을 만든다. 
  + `A`: 최상위 레벨로 컨테이너가 작동하는 OS level
    + `wsl`: 윈도우11의 wsl 환경
    + `ubuntu`: 네이티브 우분투  
  + `B`: 컨테이너 툴 
    + `podman`
    + `docker`
  + `C`: 컨테이너 내용 
    + `anari-jupyter`
    + `anari-rocker` 

## When 

- 2021-10-26 문제 인식 
- 2021-10-31 테스트 완료 

## MISC

### Rocker의 해결되지 않은 문제점 

- 플랫폼 별로 일관성이 없다. 
- 컨테이너와 연결된 볼륨의 권한 문제 
  + 파일 생성, 수정 및 삭제 불가 
- RStudio에서 프로젝트를 쓸 때 
  + permissin denied 메시지가 뜨는 경우가 있다. 