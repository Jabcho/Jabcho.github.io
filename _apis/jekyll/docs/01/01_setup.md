---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 1. Setup
이 문서는 Jekyll을 사용하기 위한 단계별 튜토리얼이다. 이 튜토리얼에서는 프론트엔드(front-end) 웹 개발 경험이 있는 사용자가 기본으로 제공되는 gem 기반 테마를 사용하지 않고 처음부터 직접 Jekyll 사이트를 만들 수 있도록 안내한다.

## Installation
Jekyll은 Ruby gem이다. 먼저 컴퓨터에 Ruby를 설치한다. 운영체제에 따른 설치 방법은 [Installation]({% link _apis/jekyll/01.md %}#installation) 페이지를 참고하라.

Ruby 설치가 완료되면, 터미널에서 아래 명령어로 Jekyll을 설치한다:


```terminal
gem install jekyll bundler
```

프로젝트의 의존성을 기록할 새로운 Gemfile을 만든다:

```terminal
bundle init
```

텍스트 에디터로 Gemfile을 열고 jekyll을 의존성으로 추가한다:

```terminal
gem "jekyll"
```

bundle 명령어를 실행해 프로젝트에 jekyll을 설치한다.

Gemfile에 정의된 jekyll 버전을 사용하기 위해서 앞으로 이 튜토리얼에서 사용하는 모든 jekyll 명령어 앞에는 bundle exec를 붙이는 것을 권장한다.

## Create a site
새로운 디렉터리를 만들고 사이트 이름을 정한다. 앞으로 이 튜토리얼에서는 이 디렉터리를 root라고 지칭한다.

여기에 Git 저장소를 초기화할 수도 있다.

Jekyll은 데이터베이스가 필요하지 않다. 모든 콘텐츠와 사이트 구조는 Git 저장소에서 버전 관리가 가능한 파일로 되어 있다. 저장소 사용은 필수는 아니지만 권장된다. 자세한 Git 사용법은 [Git Handbook](https://docs.github.com/ko/get-started/using-git/about-git)에서 확인하라.

<br>
첫 번째 파일을 추가해보자. root 디렉터리에 <code class="code-inline">index.html</code> 파일을 만들고 다음 내용을 입력한다:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

## Build
Jekyll은 정적 사이트 생성기이므로, 먼저 빌드한 후에 사이트를 볼 수 있다. 사이트를 빌드하기 위해 아래 명령어 중 하나를 실행한다:

- <code class="code-inline">jekyll build</code> - 사이트를 빌드한 후 <code class="code-inline">_site<site> 디렉터리에 정적 사이트를 출력한다.

- <code class="code-inline">jekyll serve</code> - <code class="code-inline">jekyll build</code>를 실행하고 <code class="code-inline">http://localhost:4000</code>에서
 로컬 서버를 띄운다. 이후 파일을 수정할 때마다 자동으로 사이트가 다시 빌드된다.

<div class="blue-caution">
ℹ️ 개발 중에는 <code class="code-inline">jekyll serve</code>를 사용하는 것이 편리하다. 브라우저가 변경될 때마다 자동 새로고침하려면 <code class="code-inline">jekyll serve --livereload</code>를 사용하라. 충돌이 발생하거나 다른 URL에서 개발 사이트를 실행하려면 <code class="code-inline">--host</code>와 <code class="code-inline">--port</code> 옵션을 사용할 수 있다. (자세한 내용은 [serve command options](#) 참고.)</div>

<div class="red-caution">
⚠️ <code class="code-inline">jekyll serve</code>로 <code class="code-inline">_site</code>에 빌드한 사이트 버전은 배포용으로 적합하지 않다. <code class="code-inline">jekyll serve</code>로 생성한 사이트에서는 [설정 파일(configuration file)](#)에 정의된 값이 아니라 <code class="code-inline">http://localhost:4000</code> 및 커맨드라인에서 지정한 값이 링크와 정적 자산 URL에 사용된다. 배포 준비 완료 후 사이트 배포 방법은 튜토리얼의 [배포(Deployment)](#) 섹션을 확인하라.
</div>

<code class="code-inline">jekyll serve</code>를 실행한 후 브라우저에서 http://localhost:4000
에 접속하면 “Hello World!”라는 문구가 보여야 한다.

여기까지 실행하면 단순히 Jekyll의 역할이 HTML 파일이 한 위치에서 다른 위치로 복사한 것처럼 보일 수 있으나, Jekyll의 기능은 훨씬 다양하다.

다음 단계에서는 Liquid와 템플릿(templating)을 다룬다.


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
