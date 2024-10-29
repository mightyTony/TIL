# MySQL 접속

외부 서버: mysql -h <RDS 엔드포인트> -u <DB 사용자 이름> -p

로컬 서버 : mysql -u <DB 사용자 이름> -p

# 모든 데이터베이스 조회

show databases ;

# 'board' 데이터베이스 생성

create database board;

# 로컬 호스트 서버에 'tony' 라는 이름의 유저, 비밀번호는 'password1234!@'로 생성

create user 'tony'@'localhost' identified by 'password1234!@';

# mysql 안에 생성된 유저 조회

select `user` from `mysql`.`user`;

# 로컬호스트 서버에 있는 tony 라는 유저 권한 조회

show grants for 'tony'@'localhost';

# 로컬 호스트 서버에 'tony' 라는 유저에게 'board' 테이블에 모든 데이터베이스 권한 부여

grant all on `board`.* to 'tony'@'localhost' with grant option;

# 권한 플러시(트랜젝션) 저장

flush privileges ;
