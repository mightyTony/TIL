# 1. AWS EC2 접속

스왑 메모리를 할당하려는 ec2에 접속한다.
 

# 2. swapfile 메모리 할당

128M x 16 = 2048, 2GB로 swapfile을 생성한다.
스왑 메모리는 램 메모리의 2배 또는 그 이상을 추천한다는데
프리티어를 사용하면 램은 1GB이기 때문에 스왑 메모리를 2GB로 설정했다.
sudo dd if=/dev/zero of=/swapfile bs=128M count=16
 

dd: 블록 단위로 파일을 복사하거나 파일 변환을 할 수 있는 명령어
if: 지정한 파일을 입력 대상으로 설정
of: 지정한 파일을 출력 대상으로 설정
bs: 한 번에 변환 작업 가능한 바이트 크기
count: 지정한 블록 수만큼 복사

경로는 /swapfile로 되어 있지만 원하는 경로로 설정해도 된다.
 
만약 4GB로 하려면 count를 2배로 해주면 된다.
sudo dd if=/dev/zero of=/swapfile bs=128M count=32
 

# 3. swapfile 권한 설정

2번 항목을 완료했다면 swapfile이 생성되었을 텐데
읽기, 쓰기가 가능하도록 파일의 권한을 수정한다.
sudo chmod 600 /swapfile
 

# 4. swap 공간 생성

mkswap 명령어를 사용해서 스왑 공간을 생성한다.
sudo mkswap /swapfile
 

mkswap: Make Swap의 약자로 스왑 파티션이나 스왑 파일을 생성하는 명령어

 

# 5. swapfile 스왑 메모리 추가

스왑 공간에 swapfile을 추가한다.
sudo swapon /swapfile
 
swapon 명령어가 정상으로 동작했는지 확인한다.
sudo swapon -s Filename                                Type            Size    Used    Priority/swapfile                          file            2097148 0       -2
 

swapon: 스왑으로 사용하는 파일의 경로 및 이름, 타입, 크기, 사용 중인 부분, 우선순위 등을 보여주는 명령어

 
만약 스왑 영역을 비활성화하려면 swapoff 명령어를 사용한다.
sudo swapoff -a
 

# 6. swap 파일시스템 설정

시스템 부팅 시마다 자동으로 활성화되도록 파일시스템을 수정한다.
sudo vi /etc/fstab
 
아래 내용을 추가하고 저장한다.
/swapfile swap swap defaults 0 0
 

# 7. free 명령어로 메모리 상태 확인

free 명령어를 사용해서 ec2 메모리 상태를 확인한다.
free
