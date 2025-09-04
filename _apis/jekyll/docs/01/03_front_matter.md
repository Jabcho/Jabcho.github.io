---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 3. Front Matter
Front matter는 삼중 대시(---) 두 줄 사이에 들어가는 [YAML](https://yaml.org/) 스니펫으로, 파일의 시작 부분에 위치한다.


Front matter에 페이지에서 활용할 변수를 정의할 수 있다.

```liquid
---
my_number: 5
---
```


Front matter에서 정의한 변수는 <code class="code-inline">page</code> 변수로 불러올 수 있다. 예를 들어, 위에서 정의한 <code class="code-inline">my_number</code> 값을 출력하려면 다음과 같이 작성한다:

```liquid
{% raw %}{{ page.my_number }}{% endraw %}
```

## Use front matter
Front matter를 이용하여 사이트의 <code class="code-inline">&lt;title&gt;</code> 값을 아래와 같이 바꿀 수 있다:

```liquid
---
title: Home
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
  </head>
  <body>
    <h1>{% raw %}{{ "Hello World!" | downcase }}{% endraw %}</h1>
  </body>
</html>
```

<div class="blue-caution">
ℹ️ Jekyll이 Liquid 태그를 처리하려면, 해당 페이지에 반드시 front matter가 있어야 한다.
</div>

변수를 정의하지 않고 페이지를 처리할 경우, 아래와 같이 빈 front matter를 작성한다:

```liquid
---
---
```


다음 장에서는 레이아웃(layouts)에 대해 배우고, Jekyll 페이지가 일반 HTML보다 더 많은 소스 코드를 사용하는 이유에 대해 다룰 것이다.


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
