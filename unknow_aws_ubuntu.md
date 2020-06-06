1. install miniconda
2. conda create --name app
3. install docker
curl -fsSL https://get.docker.com/ | sudo sh
4. install docker-compose
sudo curl -L https://github.com/docker/compose/releases/download/1.25.0-rc2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
5. git clone
6. django, mysql install 
apt-get install libmysqlclient-dev -y
sudo apt-get install gcc

7. make customuser model
https://dev-yakuza.github.io/ko/django/custom-user-model/

8. oauth set

9. DB router
https://chohyeonkeun.github.io/2019/06/07/190607-django-multi-database/

10. make middleware for formatted response
https://gyukebox.github.io/blog/django-커스텀-미들웨어-만들기---rest-framework-를-위한-http-response-formatting/

11. install uwsgi 
in conda env, we can't install uwsg by using "pip install uwsgi".
use "conda install -c conda-forge uwsgi"

12. auto start uwsgi
https://crazia.tistory.com/entry/Python-uwsgi-로-배포하고-우분투에서-systemd-로-관리하는-방법

