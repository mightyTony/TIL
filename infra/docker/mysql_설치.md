Docker mysql 작업환경 세팅


# docker 설치

- brew install docker 
- brew link docker
- docker version

# mysql 설치, 실행

- docker pull mysql
- docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=1234 —name mysql mysql
- docker ps

* docker : no matching manifest for linux/arm64/v8 in the manifest list entries. 오류 시 docker pull —platform linux/x86_64 mysql

# mysql 데이터베이스 생성
- docker exec -it mysql bash
- mysql -u root -p
- create database 디비이름 
- use 디비이름 
