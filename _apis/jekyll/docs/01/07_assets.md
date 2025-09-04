---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 7. Assets
Jekyll에서 CSS, JS, 이미지 같은 정적 자원(assets)을 사용하는 방법은 간단하다. 자원을 사이트 폴더에 두면, 빌드된 사이트로 그대로 복사된다.

일반적으로 Jekyll 사이트는 다음과 같은 자산 관리 구조를 가진다:

```
.
├── assets
│   ├── css
│   ├── images
│   └── js
...
```


즉, assets 폴더 안에 css, images, js 디렉터리를 만든다. 추가로, 루트(root) 바로 아래에 <code class="code-inline">_sass</code> 폴더를 하나 더 생성하라. 이 폴더는 아래에서 사용할 것이다.

## Sass
<code class="code-inline">_includes/navigation.html</code> 파일 안에 직접 스타일을 작성하거나 수정하는 방식은 권장하지 않는다. 대신 새로운 CSS 파일을 만들어 클래스(class)를 정의하고, 그 클래스를 사용해 스타일을 적용해보자.

이 다음 부분에서 정의할 클래스를 참조하기 위해, 이전 단계에서 추가했던 현재 페이지 링크를 빨간색으로 표시하던 코드를 지우고, <code class="code-inline">navigation.html</code> 파일에 다음 코드를 삽입한다:

```liquid
{% raw %}<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}"{% if page.url == item.link %} class="current"{% endif %}>{{ item.name }}</a>
  {% endfor %}
</nav>{% endraw %}
```

표준 CSS 파일을 사용할 수도 있지만, 여기서는 [Sass](https://sass-lang.com/)를 이용해 한 단계 더 나아가 볼 것이다. Sass는 CSS의 훌륭한 확장 문법으로 Jekyll에 기본적으로 내장되어 있다.

먼저, <code class="code-inline">assets/css/styles.scss</code> 파일을 만들고 다음 내용을 추가한다:

```scss
---
---
@import "main";
```

상단의 빈 Front matter는 Jekyll에게 이 파일을 처리하라고 알려준다. <code class="code-inline">@import "main"</code>은 Sass에게 sass 폴더에서 <code class="code-inline">main.scss</code> 파일을 불러오도록 지시한다. 일반적으로 이 폴더는 <code class="code-inline">_sass/</code>로, 이전에 프로젝트의 루트 디렉터리에 이미 생성해두었을 것이다.

지금 단계에서는 하나의 메인 CSS 파일만 가지게 되지만, 프로젝트가 커질수록 CSS를 정리하는 데 유용하다.

현재 페이지 링크를 초록색으로 표시하기 위해 위에서 언급한 curent 클래스를 만들어보자. _sass/main.scss 파일을 만들고 다음 내용을 추가한다:

```scss
.current {
  color: green;
}
```

레이아웃(layout)에서 이 스타일시트를 참조해야 한다.

_layouts/default.html 파일을 열고 <head> 안에 다음과 같이 스타일시트를 추가한다:

```liquid
{% raw %}<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>{% endraw %}
```

여기서 참조하는 <code class="code-inline">styles.css</code>는 앞서 <code class="code-inline">assets/css/</code> 경로에 만든 <code class="code-inline">styles.scss</code>를 Jekyll이 변환하여 생성한 파일이다.

브라우저에서 [http://localhost:4000](http://localhost:4000)에 접속해 네비게이션에서 현재 페이지 링크가 초록색으로 표시되는지 확인해보라.

다음 단계에서는 Jekyll의 대표 기능인 블로깅(blogging)에 대해 알아볼 것이다.


<h3><a href="{% link _apis/jekyll/docs/01/01_setup.md %}">1. Setup</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/02_liquid.md %}">2. Liquid</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/03_front_matter.md %}">3. Front Matter</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/04_layouts.md %}">4. Layouts</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/05_includes.md %}">5. Includes</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/06_data_files.md %}">6. Data Files</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/07_assets.md %}">7. Assets</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/08_blogging.md %}">8. Blogging</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/09_collections.md %}">9. Collections</a></h3>
<h3><a href="{% link _apis/jekyll/docs/01/10_deployment.md %}">10. Deployment</a></h3>
