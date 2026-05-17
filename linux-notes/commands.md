sudo apt update    앱최신확인
(로그인상태에서)sudo poweroff
--------------------------------
whoami 현 사용자
pwd   print working directory 현위치
ls -la 숨김파일도 보이게
cd .. 상위폴더로 이동
cd srv     현재폴더 위치에 있는 srv(service)라는 폴더로 이동
cd /srv    절대위치. srv로 이동
mkdir ~~     ~~라는 이름의 폴더 생성
touch note.txt     note.txt 파일 생성
nano note.txt     노트 편집기
ctrl O -> enter 저장
ctrl X -> 나가기
cat note.txt    파일 보기

sudo adduser testuser1     testuser1라는 user추가(후에 2번 비번 입력)
sudo userdel -r testuser1     -r하위폴더(파일,데이터)도 포함 유저삭제
ls /home     사용자확인
su - testuser1    testuser1사용자로 로그인
exit 로그아웃

sudo usermod -aG sudo testuser1      testuser1에게 관리자 권한주기

ip a -> enp0s3 -> 192.168.0.226
ssh username@192.168.0.226  in powershell      파워쉘로 VM컨트롤

oft using:
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl status nginx

VM -> 가짜 컴퓨터 전체
Docker -> 프로그램 실행 환경만 분리

----------------------------------

sudo systemctl status docker        docker 상태확인
sudo systemctl enable docker     docker 자동시작

sudo docker run -d -p 8080:80 nginx    http://ip:8080 사이트만들기
sudo docker ps     실행중인 컨테이너 보기
sudo docker ps -a     전체 컨테이너 보기
sudo docker stop (container ID)     중지
sudo docker rm (컨테이너ID)       삭제

sudo docker exec -it 컨테이너ID bash     컨테이너 안으로 들어가기

------------------------ compose 독커 긴 컨테이너를 파일로 저장해서 불러서 켜는방법
sudo mkdir -p /srv/mywebsite                         그냥 "jdwgoodya@fisilearn1:/$"여기다 만들면 권한이 없어서 srv(상위폴더?)에다가 만들어야 함.
sudo nano /srv/mywebsite/index.html         파일생성
sudo chmod -R 755 /srv/mywebsite             그리고 srv에다 권한을 줘야함
sudo docker run -d -p 8080:80 -v /srv/mywebsite:/usr/share/nginx/html nginx       영구수정가능한 docker 컨테이너

-> 그 후에 그건 간단히 compose로 하는 법 ->

sudo apt install docker-compose-v2    설치
sudo docker compose up -d    compose로 실행
sudo docker compose down     끄기 + 삭제! (깔끔)

compose의 의미 : 독커 긴 컨테이너를 파일로 저장해서 불러서 쉽게 켤 수 있다.
