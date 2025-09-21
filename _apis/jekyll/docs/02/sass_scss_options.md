---
title: Sass/SCSS Options
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
Jekyll에는 [jekyll-sass-converter](https://github.com/jekyll/jekyll-sass-converter) 플러그인이 기본으로 함께 제공된다. 기본적으로 Jekyll은 사이트의 <code class="code-inline">source</code> 디렉터리를 기준으로 하는 <code class="code-inline">_sass</code> 디렉터리에서 Sass 파셜을 찾는다.

Jekyll 설정의 <code class="code-inline">sass</code> 속성 옵션을 추가하여 플러그인을 더 세부적으로 설정할 수 있다. 자세한 내용과 기본값에 대해서는 [플러그인 문서](https://github.com/jekyll/jekyll-sass-converter#usage)를 참고하라.

<div class="blue-caution"  markdown="1">
ℹ️ VSCode에서 <code class="code-inline">@import "main";</code> 구문과 관련한 경고가 보이더라도, 이는 Jekyll에서 SCSS 코드가 동작하는 데 영향을 주지 않으므로 무시해도 된다. 다만 Jekyll 4에서는 동일한 이름의 Sass 페이지, 즉 <code class="code-inline">css/main.scss</code>에서 같은 이름의 <code class="code-inline">main</code> sass 파셜(<code class="code-inline">_sass/main.scss</code>)을 불러오는(import) 것은 허용하지 않는다.
</div>

<div class="blue-caution"  markdown="1">
ℹ️ <code class="code-inline">sass</code> 설정에 지정한 디렉터리 경로는 _config.yml 파일의 위치가 아니라, 사이트의 <code class="code-inline">source</code> 디렉터리를 기준으로 해석된다는 점에 유의하라.
</div>
