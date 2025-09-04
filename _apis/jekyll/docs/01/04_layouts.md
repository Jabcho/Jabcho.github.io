---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

## 4. Layouts
Jekyll은 페이지를 빌드할 때 HTML뿐 아니라 [Markdown](https://daringfireball.net/projects/markdown/syntax)도 지원한다.
Markdown은 HTML보다 간결하기 때문에 문단, 제목, 이미지 등만 포함한 단순한 구조의 페이지를 작성하기에 좋다.

사이트의 루트 디렉터리에 <code class="code-inline">about.md</code>라는 새 Markdown 파일을 만들어보자.

<code class="code-inline">index</code> 파일의 내용을 복사해서 About 페이지로 수정할 수도 있다. 하지만 이 경우 새로운 페이지를 추가할 때마다 복사한 코드를 별도로 수정해야 한다.

예를 들어, 사이트에 새로운 스타일시트를 추가하려면 모든 페이지의 <head>에 해당 스타일시트를 연결하는 링크를 넣어야 한다. 페이지가 많아질수록 시간이 많이 소요된다.

## Creating a layout
Layout은 사이트 내 어떤 페이지에서도 사용할 수 있는 템플릿으로, 페이지 콘텐츠를 감싸는 구조다. Layout 파일은 <code class="code-inline">_layouts</code> 디렉터리에 저장된다.

사이트의 루트 디렉터리에 <code class="code-inline">_layouts</code> 디렉터리를 만들고, 그 안에 새로운 default.html 파일을 생성한 뒤 아래 코드를 입력한다:

```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
  </head>
  <body>
    {% raw %}{{ content }}{% endraw %}
  </body>
</html>
```

이 HTML은 <code class="code-inline">index.html</code>과 거의 동일하다. 하지만 <code class="code-inline">index.html</code>에는 Front matter가 없고, <code class="code-inline">index.html</code> 페이지의 본문이 <code class="code-inline">content</code> 변수로 대체된다는 점이 다르다.

<code class="code-inline">content</code>는 호출된 페이지에서 렌더링된 본문 내용을 반환하는 특별한 변수이다.

## Use layouts
<code class="code-inline">index.html</code>에서 특정 layout을 사용하려면 Front matter에 <code class="code-inline">layout</code> 변수를 설정한다. 파일은 다음과 같이 작성할 수 있다:

```liquid
---
layout: default
title: Home
---
<h1>{% raw %}{{ "Hello World!" | downcase }}{% endraw %}</h1>
```


사이트를 다시 로드하면 출력 결과는 동일하다.

Layout은 페이지 콘텐츠를 감싸기 때문에, layout 파일 안에서도 <code class="code-inline">page</code> 객체를 이용해 적용된 페이지의 front matter 변수를 호출할 수 있다. 즉, layout을 특정 페이지에 적용하면 해당 페이지의 front matter가 사용된다.

## Build the About page
<code class="code-inline">about.md</code> 파일에 다음 내용을 추가해, 새로 만든 layout을 About 페이지에 사용해보라:

```liquid
---
layout: default
title: About
---
# About page

This page tells you a little bit about me.
```


브라우저에서 [http://localhost:4000/about.html](http://localhost:4000/about.html)로 접속해서 새로운 페이지를 확인해보자.

축하한다! 이제 두 개의 페이지를 가진 웹사이트가 완성되었다.

다음 단계에서는 페이지 간 탐색 방법을 배울 것이다.


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
