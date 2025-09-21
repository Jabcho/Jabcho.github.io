---
title: Environments
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
<code class="code-inline">build</code>(또는 <code class="code-inline">serve</code>) 명령을 실행할 때 전달하는 인자에서 Jekyll 환경과 그 값을 지정할 수 있다. 이렇게 지정한 값은 본문의 모든 조건문에서 참조되어 빌드 시 적용된다.

예를 들어 코드에 다음과 같은 조건문을 넣었다고 하자:

```liquid
{% raw %}{% if jekyll.environment == "production" %}
   {% include disqus.html %}
{% endif %}{% endraw %}
```

이제 Jekyll 사이트를 빌드할 때, 다음 예시와 같이 빌드 명령에 <code class="code-inline">production</code>환경을 함께 지정하지 않으면 <code class="code-inline">if</code> 블록 안의 내용은 실행되지 않는다:

```terminal
JEKYLL_ENV=production jekyll build
```

환경 값을 지정하면 특정 콘텐츠를 특정 환경에서만 동작하도록 할 수 있다.

<code class="code-inline">JEKYLL_ENV</code>의 기본값은 <code class="code-inline">development</code>다. 따라서 빌드 명령에서 <code class="code-inline">JEKYLL_ENV</code>를 생략하면 기본으로 <code class="code-inline">JEKYLL_ENV=development</code>가 적용된다. <code class="code-inline">{% raw %}{% if jekyll.environment == "development" %}{% endraw %}</code> 태그 안의 내용은 빌드 결과물에 자동으로 포함된다.

환경 값은 원하는 대로 지정할 수 있으며, 반드시 <code class="code-inline">development</code>나 <code class="code-inline">production</code>일 필요는 없다. 또한 개발 환경에서는 Disqus 댓글 폼이나 Google Analytics같은 요소를 숨기고, 반대로 “GitHub에서 편집하기(Edit me in GitHub)” 버튼은 개발 환경에서만 노출할 수도 있다.

빌드 명령에서 옵션을 지정함으로서, 환경을 바꿀 때마다 설정 파일의 값을 고쳐야 하는 수고를 피할 수 있다.

<div class="yellow-caution" markdown="1">
✨ 환경에 따라 일부 설정을 전환하려면 빌드 옵션 <code class="code-inline">--config, _config.yml,_config_development.yml</code> 같은 [build command option]({% link _apis/jekyll/docs/02/configuration_options.md %}#build-command-options)을 사용하라. 뒤에 나열된 파일의 앞의 파일의 설정을 덮어쓴다.
</div>
