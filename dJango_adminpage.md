---

프로젝트로 관리자 페이지를 만들게 되었습니다.

헙... 웹이라는 영역은 항상 나에게 어렵게만 느껴집니다. 뭔가.. 디버깅도 잘 안되고, 어디가 에러 인지도 모르겠고, 그놈에 404와 500 ㅋㅋㅋㅋ Spring교육에서 마이바티스를 사용해 어케어케 하는 것도 배우긴 했는데, 며칠 배우는 걸로 확 늘지 않을 거고.. 그렇다고 클라이언트 개발을 안 한 건 아닙니다. 안드, 아이폰 개발도 했고 유니티 C#으로 게임도 만들어보고... 근데 항상 웹페이지는 귀찮고 번거로운 작업으로 여겨졌습니다. 그러다가 드디어 뭔가 만들어야 하는 시간이 온 것입니다. 

이 포스팅은 정말로 1도 웹에 대해서 모르는, HTML도 모르고 JS도 모르고 CSS도 모르고! 하는 웹알못이 관리자 페이지를 만드는 과정에 대한 글입니다. 쓰면서도 이게 다른 사람들한테 도움이 될지 모르겠습니다. ㅋㅋㅋㅋㅋㅋㅋ

### ▷ 요건정의

무엇을 만들 것인가? 는 항상 중요합니다. 업무 프로세스에서 '기획'단계에 해당하는데, 뭐 개발자 나부랭이가 기획을 하진 않을 거고, 요청이 온대로 코딩할 뿐입니다. 하지만 웹페이지는 뭔가.. 개발자도 기획을 해야 될 것 같은 그런 느낌이지 않음? 나만 그럼!?

화면 디자인과 코드가 나뉘어 있는 모바일에 비해, 뭔가 웹은 두 개가 합쳐져 있는 느낌입니다. 물론 나의 느낌일 뿐, 웹 개발자들은 잘 나뉘어있다고 생각할 수도 있어요. 내가 만들 dJango 프레임워크도 화면은 뭔가 html 문서에 담겨있고, 동작 함수들은 python 문서에 있으니까..? 그래도 뭔가 html 까보면 자바 스크립트도 있고 파이썬 코드도 있어서 과연 분리된 것인지 합쳐진 것인지 모르겠습니다.

아무튼 내가 만들 관리자 페이지의 요건은 아래와 같습니다. 

1차 요건

> \- 질의응답 데이터를 관리하는 화면  
> \- 질의응답 데이터는 DB에 저장되고, 화면에 게시판 형태로 뿌려주고, 수정, 삭제, 추가가 가능해야 됨  
> \- 특정 사용자가 언제 어떤 질문을 했고 어떤 대답을 했는지 로그 형식으로 화면에 나타나야 함

요건을 보고 뭘 만드는 건지 궁금할 수도 있는데, 이 시스템은 FAQ챗봇으로 사용자가 어떤 질문을 하면 저장된 질의응답 중 가장 유사한 질문의 답변을 대답하도록 동작합니다. 이 과정에서 머신러닝이 들어가긴 하는데, 관리자 페이지에서는 상관없기 때문에 패스. 

아무튼 요구사항은 챗봇에 사용할 질의응답 데이터를 관리하고, 어떤 사용자가 어떤 질문을 했는지 보여주면 되는 겁니다. (일단은 ^^)

### ▷ 개발환경

> Web framework - dJango  
> DB - mariasql  
> OS - mac  
> TOOL - Pycharm, MySQLWorkbench

앞에서 잠깐 언급했고, 제목에도 언급돼 있듯이 웹 프레임워크는 장고(dJango)를 사용합니다. 왜 장고를 사용하냐면, 챗봇에 사용된 머신러닝 소스가 파이썬으로 되어있어서, 그 위에 웹페이지를 띄우기 위해 장고를 선택했습니다. DB는 마리아를 사용하고, 개발 OS는 맥입니다. 서비스하는 서버는 윈도우 서버긴 하지만 개발서버에서 쉽게 배포할 수 있는 환경이 아니라서 달라도 상관없어요. ^^

### ▷ 장고 설치

사실 장고는 많이 써봐서(설치만 많이 해봐서) 익숙한 느낌입니다. 아마 웹알못이면서 장고를 처음 써본다면 아주 매우 생소할 거예요. 게다가 python도 안 해봤다면 더더더 혼란이 올 겁니다. 일단 pycharm이라는 갓 젯브레인형님들이 만든 툴을 쓰면, 그나마 터미널에서 이것저것 입력하거나 가상환경 설정하는데 시간을 쏟을 필요가 없습니다. Pycharm coummunity버전은 무료이기 때문에 어서 다운 ㄱㄱ

사실 이 포스팅은 장고로 웹페이지를 만드는 목적이기 때문에 장고 튜토리얼에 대한 내용은 쓰지 않겠습니다.(사실 귀찮음)

대신 초반 설정 같은 게 잘 나와있는 링크로 대체합니다.

[https://tutorial.djangogirls.org/ko/](https://tutorial.djangogirls.org/ko/)

[

들어가며 · Django Girls Tutorial

이 튜토리얼은 열정적인 장고걸스 코치들과 자원봉사자들의 수고로 번역되었습니다. 장고걸스 튜토리얼에 오신 여러분들을 환경합니다! 이 곳에서 만나게 되어 기뻐요 :) 여러분을 웹 테크놀로지의 여정으로 초대하여 함께 조금씩 맛보면서 웹이 어떻게 작동하는지 알 수 있도록 도와드릴 거에요. 아직 발견하지 못한 것을 알아가야하는 꽤 도전적인 모험이 될 것이지만, 지금 이 튜토리얼을 보는 여러분들은 용기를 가지고 있기 때문에, 끝까지 잘 해낼 거라 믿어요. :) 점점

tutorial.djangogirls.org



](https://tutorial.djangogirls.org/ko/)

### ▷ 관리자 페이지 앱 만들기

장고를 어느 정도 배우셨다면 앱을 만든다는 게 어떤 의미인지 아실 겁니다. 장고는 앱 단위로 소스를 관리하는데, 장고 프로젝트 트리를 보면 앱단위로 폴더가 만들어져 있습니다. (물론 기본 폴더도 있습니다)

[##_Image|kage@BuwwK/btqvjLNhXB5/enzV9CvpTTk4zLNZEx1gk0/img.png|alignCenter|data-filename="스크린샷 2019-05-16 오전 10.15.39.png"|현재 프로젝트 트리_##]

제 프로젝트의 경우 adminpage, test\_server(디폴트), testweb 3개의 앱이 설치되어있습니다. 이 중에서 관리자 페이지는 adminpage앱이고 다른 두 개는 기본으로 만들어져 있던 것과 다른 사람이 만든 앱입니다. 앱 만드는 것은 터미널에서 python setting.py명령어로 가능합니다. (위에 튜토리얼 참조)

### ▷ 첫 화면 만들어보기

일단 제가 웹 전문가가 아니기 때문에 처음부터 완성된 프로젝트를 만들기 어렵습니다. 따라서 이것저것 시도해보면서 나중에 수정할 탠 대요.. 이단 관리자 페이지용으로 만든 adminpage앱을 들어갔을 때 첫 화면을 만들어보겠습니다. 장고 프레임워크에서 사용자가 특정 url로 접근했을 때 어떤 페이지를 띄울지는 urls.py소스를 참조하게 됩니다. 이 urls.py를 관리하는 것도 여러 가지 방법이 있는데, 가장 디폴트 앱 (저 같은 경우에는 test\_server)에 있는 urls.py(root urls라고 부릅니다)만 가지고 컨트롤하는 경우가 있고, 각 앱마다 urls.py를 만들어서 root url에서 참조해서 관리하는 방법이 있습니다. 이건 뭐 딱히 정해진 정답이 없으니 저는 그냥 root url에서 다 지지고 볶는 방법을 선택하겠습니다. 제 root urls.py는 아래 소스가 쓰여있습니다.

```
from django.conf.urls import url, include
from django.contrib import admin
from testweb import views as view1
from adminpage import views as view2

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^testweb/', view1.index),
    url(r'^adminpage/', view2.index, name='index_faq'),
]
```

장고의 경우 기존의 MVC모델과는 살짝 다른 구조를 가지고 있습니다. VIEW역할을 하는 것이 html인데 views.py라는 소스도 있어서 약간의 혼란을 줍니다. 일단 우리가 아는 MVC의 VIEW와 장고의 views.py는 살짝 다르다는 것만 알고 계시면 되고, views.py는 어떤 VIEW를 보여줄지 정하는 역할을 한다고 생각하면 됩니다.

위 urls.py를 보면 adminpage/라고 시작하는 url을 입력할 경우 view2.index를 호출합니다. view2는 adminpage라는 앱 안에 있는 views.py를 참조한 것으로 adminpage/views.py 안에 있는 index메서드를 호출합니다.

```
# adminpage/view.py
from __future__ import unicode_literals
from .models import Faq
from django.shortcuts import render


def index(request):
    faqs = Faq.objects.all()
    context = {'faqs' : faqs }
    return render(request, 'adminpage/index.html', context)
```

index 메소드 안에는 faqs가 있는데, context에 넣어서 html에 전달해줄 인자 값입니다. Faq를 보면 .models에서 import를 해오는데,. models는 현재 앱에 있는 models.py에서 가지고 온다는 뜻입니다. models.py를 보면 아래와 같이 선언되어 있습니다.

```
# adminpage/models.py
from __future__ import unicode_literals
from django.db import models

# Create your models here.

class Faq(models.Model):
    faq_id = models.CharField(max_length=16, default='0000000000000001')
    faq_type = models.CharField(max_length=10, default='999')
    faq_question = models.TextField(default='질문')
    faq_answer = models.TextField(default='답변')

    def __str__(self):
        return self.faq_question
```

MVC에서 Model역할과 동일한 역할을 하는 것이 장고의 models.py입니다. 저는 Faq라는 모델을 만들고 안에 4개의 필드를 선언했습니다. 이 모델을 아까 views.py에서 참조에서 Faq.objects.all() 메서드를 사용해 서버에 저장되어있는 모든 Faq객체를 adminpage/index.html로 보냅니다. 왜냐하면 adminpage/index.html에서 모든 객체를 보여주기 위해서지요.

url로 시작해서 건너 건너 models.py까지 오게 되었는데, 순서를 한번 정리해봅시다.

일단 사용자가 ~/adminpage/로 시작하는 url로 접속하면, root url에 정의된 대로 adminpage/views.py 에 있는 index를 실행합니다. index 안에는 models.py에 정의된 Faq 모양으로 모든 객체를 adminpage/index.html 페이지에 전달하게 됩니다. 최종적으로 사용자의 브라우저에는 adminpage/index.html이 보이게 됩니다.

html은 장고 프로젝트 안에 templates안에 보관되며, 앱별로 구분하기 위해 templates안에 앱별로 폴더를 만들어서 관리합니다. 따라서 adminpage/index.html의 경로는 adminpage앱 폴더 안이 아니라 templates/adminpage/index.html입니다. 그럼 이제 index.html을 만들어 볼까요?

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

</body>
</html>
```

기본적으로 pycharm에서 html문서를 만들면 위와 같이 디폴트 문서가 만들어집니다. 화면에 어떻게 나오는지 볼까요?

[##_Image|kage@KDmrD/btqvicdSnip/XCKsUPk1REMVk2vZnoS5X0/img.png|alignCenter|data-filename="스크린샷 2019-05-16 오후 1.22.54.png" width="348" height="255"|...? 텅텅_##]

디폴트라고 해서 뭐라도 뜰 줄 알았는데 아무것도 안 뜹니다.. ^^ 이제 여기에 FAQ내용을 띄워봅시다. 아까 views.py에서 Faq객체를 인자로 index.html을 호출했던 거 기억나시죠? html을 아래처럼 바꿔봅시다.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <table>
        <tr>
            <th> 코드 </th>
            <th> 타입 </th>
            <th> 질문 </th>
            <th> 답변 </th>
        </tr>
        {%  for faq in faqs %}
        <tr>
            <td>{{ faq.faq_id }}</td>
            <td>{{ faq.faq_type }}</td>
            <td>{{ faq.faq_question }}</td>
            <td>{{ faq.faq_answer }}</td>
        </tr>
        {% endfor %}
    </table>

</body>
</html>
```

<table> <tr> <th> <td> 등등.. html 태그들입니다. 표를 만들 때 사용하죠. 일일이 쓰셔도 되지만 쉽게 표 html을 뽑을 수 있는 사이트가 있길래 활용했습니다. ㅋㅋ 

요 사이트 들어가면 됩니다. 

[http://www.tablesgenerator.com](http://www.tablesgenerator.com) 

[

Create LaTeX tables online

www.tablesgenerator.com



](http://www.tablesgenerator.com)

이제 만든 html이 어떻게 출력되는지 확인해보겠습니다. ~/adminpage/에 들어가 보면 아까처럼 텅 빈 화면이 아니라...

[##_Image|kage@Sl2xm/btqvnGcQfr0/K1e80IZSZnyQ8CtHey4WT0/img.png|alignCenter|data-filename="스크린샷 2019-05-16 오후 1.44.54.png" width="762" height="434"|표를 추가한 html 출력화면_##]

위처럼 데이터가 보이게 됩니다. 데이터를 어떻게 넣었냐 하면 DB에 직접 부었습니다. models.py에 모델을 만들고 python manage.py makemigrations와 migrate를 하게 되면 models.py에 선언한 모델 형태로 DB가 만들어집니다. 아마 다른 웹서비스를 만들어보시면 이 방법이 익숙할 겁니다. ORM이라고 하는 건가? 그런 겁니다. 물론 장고에서 DB세팅도 해야 되고요. DB세팅은 settings.py에 있습니다.

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'keybot',
        'USER': 'root',
        'PASSWORD': 'password123',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

따로 설정을 안 했다면 기본적으로 sqllite3가 되어있고, 저는 위에서 마리아 DB를 사용한다고 했으니 mysql로 설정해놨습니다. 데이터를 넣을 때는 DB 툴인 MySQLWorkbench로 넣었습니다. 

[##_Image|kage@bwtqxi/btqvibTBqxG/oQ6fLpI6WmfWiMyyJjtBkk/img.png|alignCenter|data-filename="스크린샷 2019-05-16 오후 1.49.58.png"|MySQLWorkbench 화면_##]

다시 html로 돌아와서... 표가 만들어지긴 한 것 같은데 테두리가 없네요. 드디어 css란 것을 적용해야 할 때입니다. 표를 위한 css를 만들고 우리가 만든 표에 적용시키면 됩니다.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg .tg-21xh{font-weight:bold;background-color:#34cdf9;color:#333333;border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
    <table class="tg">
        <tr>
            <th class="tg-21xh"> 코드 </th>
            <th class="tg-21xh"> 타입 </th>
            <th class="tg-21xh"> 질문 </th>
            <th class="tg-21xh"> 답변 </th>
        </tr>
        {%  for faq in faqs %}
        <tr>
            <td>{{ faq.faq_id }}</td>
            <td>{{ faq.faq_type }}</td>
            <td>{{ faq.faq_question }}</td>
            <td>{{ faq.faq_answer }}</td>
        </tr>
        {% endfor %}
    </table>

</body>
</html>
```

위에 링크한 표를 만드는 사이트에서 표를 만들었다면 css도 포함되어 있을 겁니다. 위 html에서 <style></style> 부분이 css정의 부분입니다. 정의한 css를 적용시키려면 태그에 class attribut를 먹이면 됩니다. 표를 보시면 <table> 태그에 class="tg"가 추가된 게 보일 거예요. 마찬가지로 <th>에도 css를 적용했습니다. 이제 다시 html을 출력해보면...

[##_Image|kage@cmGDq7/btqvi4fsIRr/Zu5xfbM342YICgWm24Gb21/img.png|alignCenter|data-filename="스크린샷 2019-05-16 오후 1.59.18.png"|css 적용 후_##]

이제 좀 그럴듯해 보이죠? (개발자의 시선..)

### ▷ 수정, 삭제 기능 추가

객체를 출력하는 것을 만들었으니, 이제 수정이나 삭제를 만들어야 합니다. 수정하기나 삭제하기 버튼을 만들어서 누르면 팝업이 슉떠서 수정하고 삭제하면 좋을 것 같아요. 그래서 dJango에서 팝업창 만들기를 구글링 해봤는데, bootstrap을 사용하라고 많이 나와있네요. bootstrap은 또 뭘까요... ㅋㅋㅋㅋㅋ

> **Bootstrap** is the most popular **CSS Framework** for developing responsive and mobile-first websites.  
> by https://www.w3schools.com

가장 인기 있는 CSS Framework라고 합니다. 살짝 써보니까 뭔가 기본 CSS모음집? 같은 느낌입니다. 안에 버튼이나 팝업, 텍스트 필드 같은 기본적인 위젯들의 테마가 포함되어있습니다. 팝업도 이걸로 만들면 편하다길래 이참에 한번 써봤습니다. ㅋㅋㅋ

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" href="/static/bootstrap.css">
</head>
<body>
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg .tg-21xh{font-weight:bold;background-color:#34cdf9;color:#333333;border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>

    <script type="text/javascript" src="/static/bootstrap.js"></script>
    <script type="text/javascript" src="/static/jquery.bootstrap.modal.forms.js"></script>
    <div class="modal fade" tabindex="-1" role="dialog" id="modal">
        <div class="modal-dialog" role="document">
            <div class="modal-content">

            </div>
        </div>
    </div>

    <table class = "tg">
        <tr>
            <th class="tg-21xh"> 코드 </th>
            <th class="tg-21xh"> 타입 </th>
            <th class="tg-21xh"> 질문 </th>
            <th class="tg-21xh"> 답변 </th>
            <th class="tg-21xh"> 작업 </th>
        </tr>
        {%  for faq in faqs %}
        <tr>
            <td>{{ faq.faq_id }}</td>
            <td>{{ faq.faq_type }}</td>
            <td>{{ faq.faq_question }}</td>
            <td>{{ faq.faq_answer }}</td>
            <td><button id="button_1" class="update-faq btn btn-sm btn-primary" >수정</button>
                <button id="button_2" class="delete-faq btn btn-sm btn-primary" >삭제</button>
                </td>
        </tr>
        {% endfor %}
    </table>
</body>
</html>
```

일단 바로 적용해봤습니다. dJango에서 bootstrap을 쓰기 위해서 일단 pip install django-bootstrap-modal-forms으로 설치하셔야 합니다. 라이브러리를 설치하면 아마 자동적으로 bootstrap.js랑 bootstrap.css가 설치될 텐데, 경로가 어딘지 몰라서 저는 따로 다운로드하여서 프로젝트 안에 넣어놨습니다.(멍청하면 몸이 고생.. ㅋㅋㅋ) 

[##_Image|kage@bf0Jts/btqvjLNvY97/kkctNa8KmsXCGpfSUhu0HK/img.png|alignCenter|data-filename="스크린샷 2019-05-16 오후 2.14.17.png"|다운받은 js, css 파일_##]

html에서 bootstrap을 쓰려면 위 html처럼 선언하는 부분이 필요합니다. 페이지가 여러 개만 공통으로 하나 만들어놓고 불러와서 쓰기도 하는데, 저는 아직 하나니까 그냥 쌩코딩 ^^ 

선언 부분 아래쪽에 modal fade class가 있는데 이건 아마 팝업창을 선언하는 것 같습니다.(사실 먼지 잘 모름... 튜토리얼에서 하라고 했음)

그리고 표에서는 "작업"칸을 추가해서 수정 버튼과 삭제 버튼을 만들었습니다. 버튼을 보면 class=""안에 여러 가지가 선언되어있는데, bootstrap에서 제공되는 버튼 css들입니다. 자세한 사용법은 아래 링크!

[https://www.w3schools.com/whatis/whatis\_bootstrap.asp](https://www.w3schools.com/whatis/whatis_bootstrap.asp)

이제 다시 html을 출력해보면 버튼이 생긴 것을 볼 수 있습니다. 하지만 버튼을 눌러도 아무 일도 일어나지 않죠.. 이제 버튼이 눌렸을 때 어떤 일을 하게 만들어야 합니다. 제가 원하는것은 수정을 눌렀을때 팝업이 뜨면서 선택한 Faq 객체를 보여주고, 수정하는 프로세스입니다. 그러기 위해서는 일단 팝업창이 떠서 제가 선택한 Faq객체가 그 팝업창에 보여야합니다. 그러기 위해서는 Faq객체의 Form을 만들어야합니다. adminpage앱 안에 forms.py 소스를 새로 생성합니다.

```
# adminpage/forms.py
from .models import Faq
from bootstrap_modal_forms.forms import BSModalForm

class FaqForm(BSModalForm):
    class Meta:
        model = Faq
        fields = ['faq_id', 'faq_type', 'faq_question', 'faq_answer']
```

BSModalForm을 받아와서 FaqForm을 만들어줍니다. 뭔가 bootstrap에서 객체를 사용하기 위한 형태(?)를 form이라고 하고 항상 만들어줘야 하나 봅니다. (역시 웹 알못..) 이렇게 Form을 만들었으면 이제 views.py에 팝업창이 뜰 때 어떤 html을 보여줄지 연결해야 합니다.

```
# adminpage/views.py
from __future__ import unicode_literals
from .models import Faq
from .forms import FaqForm
from django.urls import reverse_lazy
from bootstrap_modal_forms.generic import BSModalCreateView, BSModalUpdateView, BSModalDeleteView
from django.shortcuts import render


def index(request):
    faqs = Faq.objects.all()
    context = {'faqs' : faqs }
    return render(request, 'adminpage/index2.html', context)


class FaqCreateView(BSModalCreateView):
    template_name = 'adminpage/create_faq.html'
    form_class = FaqForm
    success_message = 'Sucess: Faq was created'
    success_url = reverse_lazy('index_faq')


class FaqUpdateView(BSModalUpdateView):
    model = Faq
    template_name = 'adminpage/update_faq.html'
    form_class = FaqForm
    success_message = 'Sucess: Faq was update'
    success_url = reverse_lazy('index_faq')


class FaqDeleteView(BSModalDeleteView):
    model = Faq
    template_name = 'adminpage/delete_faq.html'
    success_message = 'Sucess: Faq was created'
    success_url = reverse_lazy('index_faq')
```

아까 설치한 django-bootstrap-modal-forms 라이브러리에는 BSModalCreateView, BSModalUpdateView, BSModalDeleteView라는 Bootstrap 기본 Modal들이 들어있습니다. 이를 활용해 CRUD가 가능한 Class를 생성할 수 있습니다. Create는 지금 당장은 만들지 않을 거지만 나중을 위해서 미리 만들어보았습니다. template\_name에는 html주소를 넣고 form\_class에는 이전에 정의했던 forms을 넣습니다. successmessage에는 작업에 성공했을 때 메시지를 적고 success\_url은 작업이 성공했을때 어디로 갈지를 적으면 됩니다. Update와 Delete에는 model = Faq 코드가 있는데, 수정과 삭제의 경우 사용자가 선택한 faq객체를 컨트롤하기 때문에 model변수를 만들어서 넘어온 Faq객체를 관리합니다.

위에서 index.html이 사용자 브라우저에 보여주기까지 과정을 정리했었습니다. urls -> views -> html 순이었죠. 여태까지 수정과 삭제에 대한 views만 만들었습니다. urls과 html도 순서대로 만들어 보죠.

```
# test_server/urls.py
from django.conf.urls import url, include
from django.contrib import admin
from testweb import views as view1
from adminpage import views as view2
from django.urls import path

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^testweb/', view1.index),
    url(r'^adminpage/', view2.index, name='index_faq'),
    path('update/<int:pk>', view2.FaqUpdateView.as_view(), name='update_faq'),
    path('delete/<int:pk>', view2.FaqDeleteView.as_view(), name='delete_faq'),
]
```

일단 urls.py에 update와 delete를 추가합니다. 여기서 path를 사용해서 뒤에 인자 값으로 <int:pk>를 같이 대려오게합니다. <int:pk>는 장고가 객체를 만들 때 순서대로 부여하는 primary index 같은 역할을 합니다. 각 객체별로 고유의 번호가 있기 때문에 사용자가 수정하거나 삭제할 객체의 pk값을 넘기면, 어떤 객체를 말하는지 알 수 있습니다. 아까 views.py에서 Update와 Delete는 클래스로 만들었기 때문에 as\_view()를 뒤에 붙여줍니다.

```
# templates/adminpage/update_faq.html
<form method="post" action="">
    {% csrf_token %}

    <div class="modal-header">
        <h5 class="modal-title">Update Faq</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
        </button>
    </div>

    <div class="modal-body">
        {%  for field in form %}
            <div class="form-group{%  if field.errors %} invalid{%  endif %}">

                <label for="{{  field.id_for_label }}"> {{  field.label }}</label>
                {% render_field field class="form-control" placeholder=field.label %}
                {% for error in field.errors %}
                    <p class="help-block">{{  error }}</p>
                {% endfor %}
            </div>
        {% endfor %}
    </div>

    <div class="modal-footer">
        <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        <button type="button" class="submit-btn btn btn-primary">Update</button>
    </div>

</form>
```

```
# templates/adminpage/delete_faq.html
<form method="post" action="">
    {% csrf_token %}

    <div class="modal-header">
        <h5 class="modal-title">Delete Faq</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
        </button>
    </div>

    <div class="modal-body">
        <p class="delete-text"> Do you wanna del <strong> {{ faq.faq_id }} </strong></p>
    </div>

    <div class="modal-footer">
        <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        <button type="submit" class="delete-btn btn btn-danger">Delete</button>
    </div>

</form>
```

update\_faq.html와 delete\_faq.html은 boostrap의 기본 팝업 모양입니다. 대부분 디폴트고 foot 부분에 있는 버튼만 조금 수정했습니다. update body부분에서 form안에 있는 field를 하나씩 보여주는데, field의 자료형에 따라서 알맞게 표시해줍니다. 

이제 마지막으로 index.html에서 버튼을 눌렀을 때 저 update\_faq.html과 delete\_faq.html을 보여주도록 연결하면 됩니다. 연결은 urls.py에 선언했던 path를 불러오는 것으로 실행됩니다. update와 delete를 각각 update\_faq와 delete\_faq라고 name을 선언했기 때문에 그대로 불러주면 됩니다.

```
#templates/adminpage/index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" href="/static/bootstrap.css">

</head>
<body>
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg .tg-21xh{font-weight:bold;background-color:#34cdf9;color:#333333;border-color:inherit;text-align:left;vertical-align:top}

</style>

    <script type="text/javascript" src="/static/bootstrap.js"></script>
    <script type="text/javascript" src="/static/jquery.bootstrap.modal.forms.js"></script>
    <div class="modal fade" tabindex="-1" role="dialog" id="modal">
        <div class="modal-dialog" role="document">
            <div class="modal-content">

            </div>
        </div>
    </div>

    <table class = "tg">
        <tr>
            <th class="tg-21xh"> 코드 </th>
            <th class="tg-21xh"> 타입 </th>
            <th class="tg-21xh"> 질문 </th>
            <th class="tg-21xh"> 답변 </th>
            <th class="tg-21xh"> 작업 </th>
        </tr>
        {%  for faq in faqs %}
        <tr>
            <td>{{ faq.faq_id }}</td>
            <td>{{ faq.faq_type }}</td>
            <td>{{ faq.faq_question }}</td>
            <td>{{ faq.faq_answer }}</td>
            <td><button id="button_1" class="update-faq btn btn-sm btn-primary" data-id="{% url 'update_faq' faq.pk %}">수정</button>
                <button id="button_2" class="delete-faq btn btn-sm btn-primary" data-id="{% url 'delete_faq' faq.pk %}"> 삭제 </button>
                </td>
        </tr>
        {% endfor %}
    </table>


<script type="text/javascript">
    $(function() {


        $(".update-faq").each(function () {
            $(this).modalForm({formURL: $(this).data('id')});
        });
        $(".delete-faq").each(function () {
            $(this).modalForm({formURL: $(this).data('id')});
        });

    });
</script>

</body>

</html>
```

html에서 버튼이 실행되는 부분은 맨~ 아래 $(function() ~~~ 부분입니다. 

$(".update-faq")이게 수정 버튼을 말하고 $(".delete-faq")가 삭제 버튼을 뜻합니다. 아마 class로 선언된 맨 앞부분을 따오는 것 같습니다. 웹 개발이 어려운 이유가 이런 게 어떻게 돌아가는지 잘 몰라서 어렵... 도대체 update-faq로 어떻게 저걸 찾는 거죠? ㅋㅋㅋㅋ 아무튼 이렇게 하면 실행이 됩니다.

버튼에 보면 data-id라고 있는데 요건 버튼을 눌렀을 때 선택한 객체의 pk를 저장하기 위함입니다. function()에 보면 formURL: 에 $(this).data('id')로 선택한 객체의 pk와 함께 url이 호출되는 것을 볼 수 있습니다. 만약 첫 번째 객채에 있는 수정 버튼을 누르면 formURL : url 'update\_faq' 1 이 실행될 겁니다. urls.py에서 update\_faq는 update/<int:pk>라고 선언한 걸 기억하실 겁니다. 따라서 url 'update\_faq' 1은 /update/1 이 실행되는 겁니다. update\_faq는 update\_faq.html을 부르기 때문에 1번 객체가 update\_faq.html에 form형태로 전달되게 되고 update\_faq.html 팝업에 1번 객체의 내용이 뜨고 수정할 수 있게 만들어지죠. 

생각보다 복잡하고 많은 기능들이 이 짧은 코드들 안에 함축되어있습니다. 어떻게 보면 Framework가 잘 되어있는 거고, 어떻게 보면 내부 로직을 알지 못하면 어렵게 보이기도 합니다. 이게 ORM기반 서비스의 장점이자 단점인 것 같네요. 웹이 이래서 어렵다는....

아무튼 이것까지 적용하면 이제 수정과 삭제가 가능한 관리자 페이지가 완성됩니다.

[##_Image|kage@GO765/btqvkygcp3A/bgE1hXbpsqpKMBtAn19P5K/img.gif|alignCenter|data-filename="May-16-2019 15-18-55.gif"|팝업까지 완성_##]

휴~ Bootstrap을 사용한다고는 했지만 어디에 적용했는지 모르겠고 어떻게 썼는지도 모르게 수정/삭제 팝업이 완성되었네요!

다음번엔 페이징 처리와 상단 메뉴를 만들어보겠습니다. ㅎㅎ
