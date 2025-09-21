---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 5. Includes
사이트가 어느 정도 완성되었지만, 아직 페이지 간 이동 방법이 없다. 이제 내비게이션을 추가해보자.

내비게이션은 모든 페이지에 있어야 하므로 레이아웃에 넣는 것이 적합하다. 다만 레이아웃에 직접 추가하지 말고, 이번 기회에 인클루드(Includes) 기능을 배워보자.

## Include tag
<code class="code-inline">include</code> 태그를 사용하면 <code class="code-inline">_includes</code> 폴더에 저장된 다른 파일의 내용을 가져올 수 있다. Includes는 사이트 전반에서 반복적으로 사용하는 소스 코드를 한 곳에서 관리하거나, 코드 가독성을 높이는 데 유용하다.

특히 내비게이션 코드는 복잡해질 수 있으므로, 별도의 인클루드 파일로 분리하는 것이 좋다.

## Include usage
내비게이션을 위한 <code class="code-inline">_includes/navigation.html</code> 파일을 만들고 다음 내용을 작성한다:

```html
<nav>
  <a href="/">Home</a>
  <a href="/about.html">About</a>
</nav>
```

그 다음, include 태그를 이용해 <code class="code-inline">_layouts/default.html</code>에 내비게이션을 추가한다:

```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
  </head>
  <body>
    {% raw %}{% include navigation.html %}{% endraw %}
    {% raw %}{{ content }}{% endraw %}
  </body>
</html>
```

브라우저에서 [http://localhost:4000](http://localhost:4000)에 접속하여 페이지 간 이동을 테스트해보라.

## Current page highlighting
이번에는 내비게이션에서 현재 페이지를 하이라이트하는 방법을 알아보자.

<code class="code-inline">_includes/navigation.html</code>은 내비게이션이 삽입된 페이지의 URL을 알아야 스타일을 적용할 수 있다. Jekyll은 여러 유용한 [변수](#)를 제공하는데, 그중 하나가 <code class="code-inline">page.url</code>이다.

<code class="code-inline">page.url</code>을 사용하면 각 링크가 현재 페이지인지 확인할 수 있고, 맞으면 빨간색으로 표시할 수 있다:

```liquid
{% raw %}<nav>
  <a href="/" {% if page.url == "/" %}style="color: red;"{% endif %}>
    Home
  </a>
  <a href="/about.html" {% if page.url == "/about.html" %}style="color: red;"{% endif %}>
    About
  </a>
</nav>{% endraw %}
```

이제 [http://localhost:4000](http://localhost:4000)
을 다시 열면, 현재 페이지 링크가 빨간색으로 강조되어 있는 것을 확인할 수 있다.

여전히 반복되는 코드가 많다. 예를 들어 내비게이션 항목을 새로 추가하거나 하이라이트 색상을 바꾸려면 중복된 부분을 모두 수정해야 한다. 다음 단계에서는 이 문제에 대해 다룰 것이다.


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
