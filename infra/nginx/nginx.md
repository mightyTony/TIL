# 1. Nginx 설치

# sudo apt update
# sudo apt install nginx -y

# sudo yum update -y
# sudo yum install nginx -y
Nginx 리버스 프록시 설정
Nginx 설정 파일을 수정하여 포트 80으로 들어오는 모든 요청을 포트 8080으로 전달하도록 설정합니다.

# 2. Nginx 설정 파일 열기

# sudo nano /etc/nginx/conf.d/spring.tonyworld.kr.conf
설정 파일 내용 추가

다음 내용을 추가하여 Nginx가 리버스 프록시 역할을 하도록 합니다:

```
server {
    listen 80;
    server_name spring.tonyworld.kr;

    location / {
        proxy_pass http://localhost:8080;  # Spring 애플리케이션이 실행 중인 포트
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```
# 3. Nginx 설정 테스트 및 재시작

# Nginx 설정을 저장하고 종료한 후, Nginx 설정이 올바른지 테스트합니다:

# sudo nginx -t
# sudo systemctl restart nginx

# 4. HTTPS 설정 (선택 사항)
보안을 강화하기 위해 Let's Encrypt를 사용하여 무료 SSL 인증서를 설치하고 HTTPS로 리다이렉트하는 것도 좋은 방법입니다.

Certbot 설치

# sudo apt install certbot python3-certbot-nginx -y

# 5. SSL 인증서 발급 및 설정

# sudo certbot --nginx -d spring.tonyworld.kr

----
##  재발급 자동화 

# 1. cron 설치
crontab을 사용하려면 먼저 cron 패키지를 설치해야 합니다. 다음 명령어를 사용하여 cron을 설치합니다.

sudo yum install cronie -y

# 2. cron 서비스 시작 및 활성화
cron이 설치되면, 서비스를 시작하고 부팅 시 자동으로 시작되도록 설정해야 합니다.

sudo systemctl start crond
sudo systemctl enable crond

# 3. 자동 갱신을 위한 crontab 설정
이제 crontab을 사용하여 Certbot 인증서 갱신을 자동화하는 스케줄을 설정할 수 있습니다:

sudo crontab -e
crontab 편집기가 열리면 다음 라인을 추가하여 Certbot 자동 갱신을 설정합니다:

0 2 * * * /usr/bin/certbot renew --quiet
이 설정은 매일 새벽 2시에 Certbot이 인증서를 갱신하도록 합니다.

# 4. crontab 설정 확인

sudo crontab -l
이 명령어는 현재 사용자(root)의 crontab에 설정된 작업을 나열합니다.

# 5. 갱신 테스트

sudo certbot renew --dry-run
