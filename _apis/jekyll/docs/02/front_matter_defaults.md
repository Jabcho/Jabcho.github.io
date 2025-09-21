---
title: Front Matter Defaults
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
[Front matter]({% link _apis/jekyll/03.md %}#front-matter)를 사용하여 페이지와 게시글 설정을 지정할 수 있다. 기본 레이아웃을 지정, 제목(title) 커스터마이징, 게시글의 정확한 날짜/시간 지정 등을 할 수 있다.

종종 동일한 설정을 여러 번 반복하는 일이 발생한다. 예를 들어 모든 파일에 같은 layout을 지정하거나, 게시글에 한 개 이상의 동일한 카테고리를 추가하는 식이다. 심지어 동일한 저자명(author names) 등 대부분의 블로그 게시글에서 같을 확률이 높은 사용자 정의 변수를 매번 추가하기도 한다.

새 게시글이나 페이지를 만들 때마다 이와 같은 설정을 반복하지 않도록, Jekyll에서는 사이트 설정에 기본값을 정의하는 방법을 제공한다. 이를 위해 프로젝트 루트 디렉터리의 <code class="code-inline">_config.yml</code> 파일에서 <code class="code-inline">defaults</code> 키를 사용해 사이트 전역 기본값을 지정할 수 있다.

<code class="code-inline">defaults</code> 키에는 특정 파일 경로(필수)와 파일 유형(선택)에 적용할 기본값을 정의하는 scope/values 쌍의 배열이 들어간다.

예를 들어, 사이트의 모든 페이지와 게시글에 기본(default) 레이아웃을 지정하려면 <code class="code-inline">_config.yml</code>에 다음과 같이  추가한다:

```yaml
defaults:
  -
    scope:
      path: "" # 빈 문자열은 프로젝트의 모든 파일을 의미
    values:
      layout: "default"
```

<div class="blue-caution">
ℹ️ **`jekyll serve` 중단 후 재실행.**
<code class="code-inline">_config.yml</code>(루트 설정 파일)에는 전역 설정과 변수 정의가 포함되어 있으며, Jekyll은 실행 시 이 파일을 한 번만 읽는다. 자동 재생성(automatic regeneration) 중에 <code class="code-inline">_config.yml</code>을 변경해도 다음 실행 전까지 반영되지 않는다.
참고로 데이터 파일은 자동 재생성 동안에도 다시 로드된다.
</div>

여기서 <code class="code-inline">scope</code> 경로에 존재하는 모든 파일은 <code class="code-inline">values</code>의 적용 범위에 포함된다. path가 빈 문자열로 설정되면, 프로젝트의 **모든 파일**에 적용된다. 이 때 CSS 파일 등 일부 파일에는 동일한 layout을 적용하지 않으려면 <code class="code-inline">scope</code> 키 아래 <code class="code-inline">type</code> 값을 지정할 수 있다.

```yaml
defaults:
  -
    scope:
      path: ""       # 프로젝트의 모든 파일
      type: "posts"  # Jekyll 2.2에서는 `post`
    values:
      layout: "default"
```

이제 type이 <code class="code-inline">posts</code>인 파일에만 레이아웃이 적용된다. 사용 가능한 type 값은 <code class="code-inline">pages</code>, <code class="code-inline">posts</code>, <code class="code-inline">drafts</code>, 그리고 사이트에 정의한 모든 컬렉션(collection)이다. <code class="code-inline">type</code>은 선택 사항이지만, <code class="code-inline">scope/values</code> 쌍을 만들 때 <code class="code-inline">path</code> 값은 반드시 지정해야 한다.

앞서 언급했듯이, <code class="code-inline">defaults</code>에는 여러 개의 scope/values 쌍을 설정할 수 있다.

```yaml
defaults:
  -
    scope:
      path: ""
      type: "pages"
    values:
      layout: "my-site"
  -
    scope:
      path: "projects"
      type: "pages"   # Jekyll 2.2에서는 `page`.
    values:
      layout: "project"  # 이전 default 레이아웃을 덮어씀.
      author: "Mr. Hyde"
```

defaults에 따르면 모든 페이지는 <code class="code-inline">my-site</code> 레이아웃을 사용한다. 그러나 <code class="code-inline">projects/</code> 경로에 있는 모든 HTML 파일은 <code class="code-inline">project</code> 레이아웃을 사용할 것이다. 또한 이 파일들은 <code class="code-inline">Mr.Hyde</code>로 설정된 <code class="code-inline">page.author</code> [liquid 변수]({% link _apis/jekyll/04.md %}#variables)를 갖게 된다.

```yaml
collections:
  my_collection:
    output: true

defaults:
  -
    scope:
      path: ""
      type: "my_collection" # 사이트 컬렉션(주로 복수형)
    values:
      layout: "default"
```

이 예시의 경우, <code class="code-inline">my_collection</code> 이름을 가진 컬렉션에서는 layout이 default로 설정된다.

### Glob patterns in Front Matter defaults
defaults 값을 매칭할 때 glob 패턴을 사용할 수 있다(현재는 <code class="code-inline">*</code> 포함 패턴만 지원). 예를 들어, 다음과 같이 section 폴더의 어느 하위 폴더에 있든 <code class="code-inline">special-page.html</code>에 대해서는 특정 레이아웃을 지정할 수 있다. <span class="ver-badge">3.7.0</span>

```yaml
collections:
  my_collection:
    output: true

defaults:
  - 
    scope:
      path: "section/*/special-page.html"
    values:
      layout: "specific-layout"
```

<div class="red-caution">
⚠️ **Globbing과 성능**
패턴에 맞는 경로를 탐색(globbing)할 경우 성능에 부정적 영향을 줄 수 있다고 알려져 있으며, 특히 Windows 환경에 최적화가 충분히 되어 있지 않다는 점에 유의해라. 또한 globbing을 사용하면, 해당 컬렉션 디렉터리의 규모에 비례해 빌드 시간이 증가한다
</div>

### Precedence
Jekyll은 <code class="code-inline">_config.yml</code> 파일의 <code class="code-inline">defaults</code> 섹션에 지정한 모든 설정을 적용한다. 이때 scope에 더 구체적인 path를 지정하면, 다른 scope/values 쌍에서 설정한 값을 덮어쓸 수 있다.

위에서 다룬 두 번째부터 마지막 예시를 다시 살펴보자. 먼저 사이트 전역의 기본 페이지 레이아웃을 <code class="code-inline">my-site</code>로 지정하고, 이후 더 구체적인 경로를 지정하여 <code class="code-inline">projects/</code> 하위 경로에 있는 페이지의 기본 레이아웃을 <code class="code-inline">project</code>로 지정하였다. 이 방식은 layout 뿐 아니라 페이지나 포스트의 Front matter에서 설정할 수 있는 모든 값에 동일하게 적용할 수 있다.

마지막으로, <code class="code-inline">_config.yml</code>의 <code class="code-inline">defaults</code> 섹션에 추가한 사이트 전역 기본값은 포스트나 페이지 파일에서 덮어쓸 수 있다. 다음 예시와 같이 덮어쓰려는 설정을 해당 포스트나 페이지의 Front matter에 명시하면 된다:

```yaml
# In _config.yml
...
defaults:
  -
    scope:
      path: "projects"
      type: "pages"
    values:
      layout: "project"
      author: "Mr. Hyde"
      category: "project"
...
```

```yaml
# In projects/foo_project.md
---
author: "John Smith"
layout: "foobar"
---
The post text goes here...
```

위 설정으로 사이트를 빌드하면, <code class="code-inline">projects/foo_project.md</code>의 <code class="code-inline">layout</code>은 <code class="code-inline">project</code> 대신 <code class="code-inline">foobar</code>로, <code class="code-inline">author</code>는 <code class="code-inline">Mr. Hyde</code>가 아니라 <code class="code-inline">John Smith</code>로 적용된다.
