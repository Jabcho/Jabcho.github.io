---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 2. Liquid
Liquid는 템플릿 언어로, 크게 세 가지 주요 요소로 이루어져 있다:

- [2. Liquid](#2-liquid)
- [Objects](#objects)
- [Tags](#tags)
- [Filters](#filters)
- [Use Liquid](#use-liquid)

## Objects
{% raw %}
객체는 Liquid가 미리 정의된 변수를 페이지의 콘텐츠로 출력하도록 한다. 객체는 중괄호 두 개({{ }})로 감싸서 사용한다.
{% endraw %}

예를 들어, \{\{ page.title \}\}는 page.title 변수를 출력한다.


## Tags
{% raw %}
태그는 템플릿의 로직과 제어 흐름을 정의한다. 태그는 중괄호와 퍼센트 기호({% %})로 감싼다.
{% endraw %}

예시:

```liquid
{% raw %}{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}{% endraw %}
```

이 코드는 <code class="code-inline">show_sidebar</code> 페이지 변수가 true일 경우에만 사이드바를 표시한다.

Jekyll에서 사용할 수 있는 태그는 [여기]({% link _apis/jekyll/docs/01/tags_filters.md %})에서 확인할 수 있다.

## Filters
Filters는 Liquid 객체의 출력 결과를 바꿀 수 있다. 필터는 출력 구문 내부에서 <code class="code-inline">|</code> 기호로 구분해 사용한다.

예시:
```liquid
{% raw %}{{ "hi" | capitalize }}{% endraw %}
```

이 코드는 <code class="code-inline">hi</code> 대신 <code class="code-inline">Hi</code>를 출력한다.

더 많은 필터에 대해서는 [여기]({% link _apis/jekyll/docs/01/liquid_filters.md %})서 확인할 수 있다.

## Use Liquid

이제 Liquid를 이용해 [Setup]({% link _apis/jekyll/docs/01/01_setup.md %}) 단계에서 작성한 <code class="code-inline">Hello World!</code> 텍스트를 소문자로 바꿔보자:

```liquid
<h1>{% raw %}{{ "Hello World!" | downcase }}{% endraw %}</h1>
```

Jekyll이 이 코드를 처리하도록 하려면, 문서 상단에 [front matter]({% link _apis/jekyll/docs/01/03_front_matter.md %})를 추가해야 한다:

```liquid
# front matter는 Jekyll이 Liquid를 처리하게 만든다
```


HTML 문서는 다음과 같이 되어야 한다:

```liquid
---
---

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>{% raw %}{{ "Hello World!" | downcase }}{% endraw %}</h1>
  </body>
</html>
```

브라우저를 새로고침하면 <code class="code-inline">hello world!</code>가 보일 것이다.

Liquid와 다른 기능들을 결합할 때 Jekyll의 강력한 기능들을 효과적으로 사용할 수 있다. 단 Jekyll이 Liquid를 처리하려면 반드시 front matter를 추가해야 한다.

다음 단계에서 front matter에 대해 다룰 것이다.


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
