---
title: Liquid Options
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
Liquid의 오류 처리 방식은 <code class="code-inline">error_mode</code>로 설정할 수 있다. 옵션은 다음과 같다:

- <code class="code-inline">lax</code> — 모든 오류를 무시한다.

- <code class="code-inline">warn</code> — 오류가 발생할 때마다 콘솔에 경고를 출력한다.(기본값)

- <code class="code-inline">strict</code> — 오류 메시지를 출력하고 빌드를 중단한다.

_config.yml의 기본 설정은 다음과 같다:

```yaml
liquid:
  error_mode: warn
```

위 예시는 기본적으로 <code class="code-inline">error_mode: warn</code>으로 설정된 상태를 보여준다. 이 설정에서는 빌드 과정에서 문제가 있으면 경고로 알려 주지만, 가능하다면 빌드는 계속 진행된다.

또한 Liquid의 렌더러가 값이 할당되지 않은 변수나 존재하지 않는 필터를 잡아내도록 <code class="code-inline">strict_variables</code> 또는 <code class="code-inline">strict_filters</code>를 각각 <code class="code-inline">true</code>로 설정할 수 있다. <span class="ver-badge">3.8.0</span>

<code class="code-inline">error_mode</code>는 Liquid의 파서(parser), <code class="code-inline">strict_variables</code>와 <code class="code-inline">strict_filters</code>는 Liquid의 렌더러(renderer) 동작을 설정하기 때문에 두 설정은 서로 독립적(orthogonal)이라는 점을 기억하라.

_config.yml에서의 설정 예시는 다음과 같다:

```yaml
liquid:
  error_mode: strict
  strict_variables: true
  strict_filters: true
```

위와 같이 구성하면 build/serve가 진행되지 않으며, 문제가 된 오류를 출력한 뒤 즉시 중단한다. 이는 빌드나 서버 실행을 중단하고 liquid 관련 이슈를 확실히 파악/해결하는데 도움이 된다.
