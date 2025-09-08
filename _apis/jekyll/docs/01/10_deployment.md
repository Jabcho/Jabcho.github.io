---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 10. Deployment
마지막 단계에서는 사이트를 배포하기 위한 방법을 알아볼 것이다.

## Gemfile
사이트에 [Gemfile]({% link _apis/jekyll/01.md %}#gemfile)을 두는 것을 권장한다. 이렇게 하면 Jekyll과 다른 gem 버전을 환경과 무관하게 일관되게 유지할 수 있다.

이 튜토리얼의 1단계를 완료했다면 이미 Gemfile이 있을 것이다. 1단계를 건너뛰었다면, 루트 디렉터리에 <code class="code-inline">Gemfile</code>을 만들어라. Bundler로 Gemfile을 만들고 <code class="code-inline">jekyll</code> gem을 추가한다:

```terminal
bundle init
bundle add jekyll
```

Gemfile은 다음과 같은 형태를 지닌다:

```
# frozen_string_literal: true
source "https://rubygems.org"

gem "jekyll"
```

Bundler는 gem을 설치하고, 이후 <code class="code-inline">bundle install</code>을 실행하더라도 현재 gem 버전을 사용할 수 있도록 고정하는 <code class="code-inline">Gemfile.lock</code>을 생성한다. 추후 gem 버전을 업데이트하고 싶다면 <code class="code-inline">bundle update</code>를 실행한다.

<code class="code-inline">Gemfile</code>을 사용할 때, <code class="code-inline">jekyll serve</code> 같은 명령은 앞에 <code class="code-inline">bundle exec</code>을 붙인다. 즉 전문은 다음과 같다:

```terminal
bundle exec jekyll serve
```

이렇게 하면 Ruby 실행 환경이 <code class="code-inline">Gemfile</code>에 지정된 gem만 사용하도록 제한할 수 있다.

참고: 깃허브 페이지(GitHub Pages)로 배포할 경우, <code class="code-inline">Gemfile</code>에서 <code class="code-inline">jekyll</code> 대신 <code class="code-inline">github-pages</code> gem을 사용하면 깃허브 페이지의 배포 버전과 맞출 수 있다. 이때 깃허브 페이지는 <code class="code-inline">Gemfile.lock</code>을 무시하므로, 해당 파일을 저장소에서 제외하는 것도 고려해볼 수 있다.

## Plugins
Jekyll 플러그인을 사용하면 사이트 전용 커스텀 콘텐츠를 만들 수 있다. 이미 유용한 [플러그인](#)들이 많이 있고, 직접 만들어 사용할 수도 있다.

다음은 거의 모든 Jekyll 사이트에서 유용한 세 가지의 공식 플러그인이다:

- [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap) — 검색 엔진 색인을 돕는 sitemap 파일 생성

- [jekyll-feed](https://github.com/jekyll/jekyll-feed) — 게시글용 RSS 피드 생성

- [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag) — SEO에 도움이 되는 메타 태그 추가

이 플러그인들을 사용하기 위해서 다음과 같이 <code class="code-inline">Gemfile</code>에 추가한다. <code class="code-inline">jekyll_plugins</code> 그룹에 넣으면 Jekyll에 의해 자동으로 로드된다:

```
source "https://rubygems.org"

gem "jekyll"

group :jekyll_plugins do
  gem "jekyll-sitemap"
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end
```

그리고 <code class="code-inline">_config.yml</code>에 다음을 추가한다:

```yaml
plugins:
  - jekyll-feed
  - jekyll-sitemap
  - jekyll-seo-tag
```

이제 <code class="code-inline">bundle update</code>를 실행하여 플러그인을 설치한다.

<code class="code-inline">jekyll-sitemap</code>은 별도 설정 필요없이 빌드 시 자동으로 sitemap을 만든다.

<code class="code-inline">jekyll-feed</code>와 <code class="code-inline">jekyll-seo-tag</code>는 <code class="code-inline">_layouts/default.html</code>에 태그를 추가해야 한다:

```liquid
{% raw %}<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
    {% feed_meta %}
    {% seo %}
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>{% endraw %}
```

Jekyll 서버를 재시작하여 <code class="code-inline"><head></code>에 해당 태그들이 추가되었는지 확인한다.

## Environments
개발에서는 사용하지 않고 배포 시에만 출력하고 싶은 경우도 있을 수 있다. 대표적으로 분석 스크립트(Analytics scripts)가 그렇다.

이럴 때 [환경(environments)]({% link _apis/jekyll/docs/02/environments.md %})을 사용한다. 명령 실행 시 <code class="code-inline">JEKYLL_ENV</code> 환경 변수를 사용해 환경을 설정할 수 있다:

```terminal
JEKYLL_ENV=production bundle exec jekyll build
```

<code class="code-inline">JEKYLL_ENV</code>의 기본값은 development이다. <code class="code-inline">JEKYLL_ENV</code>를 통해 Liquid에서 <code class="code-inline">jekyll.environment</code>를 사용할 수 있다. 따라서 배포시에만 분석 스크립트를 출력하려면 다음과 같이 할 수 있다:

```liquid
{% raw %}{% if jekyll.environment == "production" %}
  <script src="my-analytics-script.js"></script>
{% endif %}{% endraw %}
```

## Deployment
마지막 단계는 사이트를 운영 서버에 올리는 일이다. 가장 기본적인 방법은 프로덕션 빌드를 실행한 후, 생성된 <code class="code-inline">_site</code> 폴더의 내용을 서버로 복사하는 것이다:

```terminal
JEKYLL_ENV=production bundle exec jekyll build
```

<div class="red-caution">
⚠️ 출력 디렉터리는 사이트 빌드시 정리된다.

사이트를 빌드하면 기본적으로 <code class="code-inline">_site</code>의 내용물이 자동으로 정리된다. 즉, 사이트 빌드 과정에서 생성되지 않은 파일이나 폴더들은 제거된다.
<br>
필요한 파일이 있다면 <code class="code-inline">keep_files</code> 설정 키를 이용해 보존할 수 있다. 또는 해당 파일을 assets 디렉터리에 두어 보존할 수도 있다.
</div>

보다 나은 방법은 [CI]({% link _apis/jekyll/docs/01/automated_deployment.md %})나 [서드파티(3rd party)]({% link _apis/jekyll/docs/01/3rd_party.md %}) 서비스로 이 과정을 자동화하는 것이다.

## Wrap up
이것으로 단계별 튜토리얼을 마치고, 이제 Jekyll 여정의 시작이다!

- [커뮤니티 포럼](https://talk.jekyllrb.com/)에서 인사 나누기

- Jekyll 개선에 [기여]({% link _apis/jekyll/docs/01/contributing.md %})하기 

- 계속 Jekyll 사이트를 만들어 보기!
