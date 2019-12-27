# AWS, Jenkins, Docker
Django 환경을 AWS와 Docker, Jenkins로 만들어보자.

1. AWS EC2 인스턴스 생성
2. Jenkins 다운로드
3. systemstl로 jenkins 구동 후 8080 방화벽 작업 (aws)
4. python3 설치 `sudo yum install python3`
5. django 프로젝트 클론해서 실행
6. 가상환경 만들기
7. sqlite3가 또 먹통되서 postgre 설치하기로함
8. `docker pull postgres`로 이미지 다운로드.
9. docker run for postres with options.
```
docker run --rm --name pgsql -e POSTGRES_DB=dbname -e POSTGRES_USER=user -e POSTGRES_PASSWARD=pwd postgres
```
docker-compose에서 name 사용.

10. DB 설정했으니 이제 다시 장고 실행 가능.

![스크린샷 2019-12-27 오후 4 39 10](https://user-images.githubusercontent.com/14961794/71507397-b942ff00-28c7-11ea-87fc-cab3cbff4f29.png)

![스크린샷 2019-12-27 오후 4 42 30](https://user-images.githubusercontent.com/14961794/71507447-e55e8000-28c7-11ea-8842-4f3d2501220e.png)

