# Macos with docker-compose 

## Why 

- M1 macos에서 도커-컴포즈를 어떻게 쓰는지 알아보자. 
- arm64 기반 이미지 테스트 

## What 

- jupyter stacks 중에서 M1에서 잘 작동하는 이미지 파악 

https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html

- 각 이미지의 차이에 관해서도 알아보자. 
    + 보통 datascience-notebook을 많이 썼는데, scipy를 써도 일단 큰 문제는 없을 것 같다. 
- 공식적으로 datascience-notebook, tensorflow-notebook 두 개가 제대로 돌지 않고 있다고 밝힌 바 있다. 