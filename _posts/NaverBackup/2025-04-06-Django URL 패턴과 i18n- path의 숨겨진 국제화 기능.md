---
title: "Django URL 패턴과 i18n: path의 숨겨진 국제화 기능"
date: 2025-04-06
categories:
 - Memo
naver_url: https://blog.naver.com/rage147-owo/223824321425
---

Django에서 urlpattenrs를 지정할 때, path 메소드를 사용한다. [문서](https://docs.djangoproject.com/en/4.2/ref/urls/#django.urls.path)

path메소드의 인수는 URL패턴을 가지게 될 String이거나 gettext\_lazy형이 들어간다.

String은 알겠지만 gettext\_lazy은 모르기에 찾아보았다.

gettext\_lazy는 i18n 국제회를 위한 도구이다.

i18n에 대해 처음 알게 되었는데, Internationalization(국제화)의 앞글자, I와 N 사이 18글자가 있다 하여 이름붙여졌다. 이러한 명명법에 관해서 재미있는 이야기를 하나 알게 되었는데, 1980년대경 미국 회사였던 Digital Equipment Corporation사의 Jan Scherpenhuizen이라는 이름의 직원이, 새로운 이메일을 발급받아야 했는데, 이름이 너무 길기때문에 관리팀에서 S12n이라는 이름을 주었다고 한다 ㅋㅋ

<http://www.i18nguy.com/origini18n.html>

i18n에 관한 더 많은 정보들

<https://www.techtarget.com/whatis/definition/internationalization-I18N>

<https://developers.google.com/international>

i18n을 어디서, 누가 먼저 만들었는지는 찾지 못했지만, 1980년대부터 국제화를 위한 it기업들의 움직임으로 파생된 단어임을 알 수 있다.

다시 Django로 돌아와서,

Django도 다양한 i18n을 지원하는데, 그 중 하나로 urlpatten도 지원된다.

즉 사용자의 요청 시점에 사용자의 언어에 따라 URL이 동적으로 바뀔 수 있다는 점을 의미한다.

URL patten은 아래와 같이 사용할 수 있다

```
from django.urls import include, path

urlpatterns = [
    url(_(r'^about/'), about_view, name='about'),

    path("index/", views.index, name="main-view"),
    path("bio/<username>/", views.bio, name="bio"),
    path("articles/<slug:title>/", views.article, name="article-detail"),
    path("articles/<slug:title>/<int:section>/", views.section, name="article-section"),
    path("blog/", include("blog.urls")),
    ...,
]
```