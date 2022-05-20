# docker 파일 생성

* FORM node:14
    - 베이스 이미지 선택, 서비스에서 필요한 기본 도커 이미지 콜론뒤 값은 버전이며 입력하지 않으면 가장 마지막 버전을 사용함

* WORKDIR /app
    - 도커네 작업 디렉토리 지정

* COPY package.json .
    - dockerfile 있는 경로의 해당 파일을 도커 이미지내 작업 경로에 복사

* RUN npm install
    - 명령어 수행, 도커 이미지내 작업 경로에 있는 packege.json 파일로 node 종속 라이브리 설치

* COPY . .
    - 현재 위치의 모든 파일을 도커 이미지내 작업 경로에 복사

* EXPOSE 3000
    - 도커 서비스의 포트를 외부노출 시킴

* CMD ["node", "app.mjs"]
    - 도커내에서 실행 명령 수행

# 이미지 빌드

* docker build .
    - dockerfile 파일이 있는 위치에서 명령 실행하면 이미지 생성 됨
    
# 도커 이미지 확인

* docker image ls
    - image list 출력

# 도커 컨테이너 실행

* docker run -p 8080:3000 [image id or name]
    - 외부에서 접근 할 8080 포트와 도커내 서비스 포트 3000 매핑하여 이미지를 컨테이너로 실행
# 실행중인 도커 컨테이너 확인

* docker ps
