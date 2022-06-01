# Docker &amp; Kubernetes  

[udemy learn 2022](https://www.udemy.com/course/docker-kubernetes-2022/)

## Contents

- [Docker](#docker)
  - [DockerFile](#dockerfile)
  - [Base Command](#base-command)
    - [Build](#build)
    - [Image](#image)
    - [Container](#container)
  - [Docker Compose](#docker-compose)
- [Kubernates](#kubernates)

## Docker

### DockerFile

[doc.docker.com/best-practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
[doc.docker.com/builder](https://docs.docker.com/engine/reference/builder/)

- filename : Dockerfile
- sample

```text
    FORM node:14            // 베이스 이미지 선택, 서비스에서 필요한 기본 도커 이미지 콜론뒤 값은 버전이며 입력하지 않으면 가장 마지막 버전을 사용함
    WORKDIR /app            // 도커내 작업 디렉토리 지정
    COPY package.json .     // dockerfile 있는 경로의 해당 파일을 도커 이미지내 작업 경로에 복사
    RUN npm install         // 명령어 수행, 도커 이미지내 작업 경로에 있는 packege.json 파일로 node 종속 라이브리 설치
    COPY . .                // 현재 위치의 모든 파일을 도커 이미지내 작업 경로에 복사
    EXPOSE 3000             // 도커 서비스의 포트를 외부노출 시킴
    CMD ["node", "app.mjs"] // 도커내에서 실행 명령 수행
```

### base-command

[doc.docker.com/docker](https://docs.docker.com/engine/reference/commandline/docker/)

#### Build

[doc.docker.com/build](https://docs.docker.com/engine/reference/commandline/build/)

- docker build .
  - Dockerfile 파일이 있는 위치에서 명령 실행하여 이미지 생성

- docker build . -t first-docker
  - -t 옵션으로 이미지 태그명을 지정해서 생성

#### Image

[doc.docker.com/image](https://docs.docker.com/engine/reference/commandline/image/)

- docker image ls
  - image list 출력

```bash
kyungmun@Kyungmun-of-MacBookAir$ docker image ls
REPOSITORY                                      TAG       IMAGE ID       CREATED         SIZE
<none>                                          <none>    6c82da82e9d8   10 days ago     950MB
<none>                                          <none>    cfb3d0ead867   10 days ago     950MB
docker.elastic.co/elasticsearch/elasticsearch   7.12.1    d090d5af83ca   13 months ago   894MB
```

#### Container

##### run

[doc.docker.com/run](https://docs.docker.com/engine/reference/commandline/run/)

- docker run -p 8080:3000 [image id or name]
  - 외부에서 접근 할 8080 포트와 도커내 서비스 포트 3000 매핑하여 이미지를 컨테이너로 실행
  - image 는 dockerhub 또는 로컬에 있는 이미지

- docker run -it [image id or name]
  - -it 옵션으로 인터렉션 가능한 쉘 모드 제공하면서 컨테이너 실행

##### ps

[doc.docker.com/ps](https://docs.docker.com/engine/reference/commandline/ps/)

- docker ps
  - 실행중인 컨테이너 보기

```bash
kyungmun@Kyungmun-of-MacBookAir$ docker ps                    
CONTAINER ID   IMAGE          COMMAND                  CREATED       STATUS         PORTS                NAMES
9171fbbfd920   cfb3d0ead867   "docker-entrypoint.s…"   10 days ago   Up 2 seconds   0.0.0.0:80->80/tcp   flamboyant_hertz
```

- docker ps -a
  - 모든 컨테이너 보기 (실행 중지된 컨테이너 포함)

```bash
kyungmun@Kyungmun-of-MacBookAir$ docker ps -a      
CONTAINER ID   IMAGE                                                  COMMAND                  CREATED         STATUS                       PORTS     NAMES
9171fbbfd920   cfb3d0ead867                                           "docker-entrypoint.s…"   10 days ago     Exited (137) 10 days ago               flamboyant_hertz
7525672b3204   cfb3d0ead867                                           "docker-entrypoint.s…"   10 days ago     Exited (137) 10 days ago               unruffled_boyd
bbfc36eb798b   docker.elastic.co/elasticsearch/elasticsearch:7.12.1   "/bin/tini -- /usr/l…"   13 months ago   Exited (143) 12 months ago             elasticsearch
```

##### etc

- docker start [컨테이너ID or NAME]
  - 지정 컨테이너 재시작 (중지된 컨테이너)
- docker stop [컨테이너ID or NAME]
  - 지정 컨테이너 중지
- docker rm [컨테이너ID or NAME]
  - 지정한 컨네이너 삭제 (중지 되어있어야 함)
- docker container prune
  - 중지된 모든 컨테이너 삭제

```bash
kyungmun@Kyungmun-of-MacBookAir$ docker container prune       
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
7525672b32046070cfaaeb3065c4ac45e80720697c8b55d553ee5f881cf9eec1
bbfc36eb798b26280ee6f54ee940fb01f6e213552be8a8c6c36d6380ea824c17

Total reclaimed space: 378.1kB
```

### Docker-compose

---

## Kubernates
