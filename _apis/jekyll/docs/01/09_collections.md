---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 9. Collections
이번에는 각 저자별로 프로필과 발행한 글 목록을 보여주는 개별 페이지를 갖도록 저자 정보를 구체화해보자.

이를 위해 컬렉션(Collections) 기능을 사용한다. 컬렉션은 게시글(posts)과 유사하지만, 날짜 기준으로 그룹화하지 않아도 된다.

## Configuration
컬렉션을 사용하려면 먼저 Jekyll에 해당 정보를 알려야 한다.
Jekyll 설정은 기본적으로 루트 디렉터리의 <code class="code-inline">_config.yml</code> 파일에서 할 수 있다.

루트 디렉터리에 <code class="code-inline">_config.yml</code> 파일을 만들고 다음과 같이 작성한다:

```yaml
collections:
  authors:
```

설정을 (재)로드하려면 Jekyll 서버를 재시작해야 한다.
터미널에서 <code class="code-inline">Ctrl</code>+<code class="code-inline">C</code>를 눌러 서버를 중단한 뒤, <code class="code-inline">jekyll serve</code>를 실행하여 재시작한다.

## Add authors
컬렉션에 포함되는 각 문서(document)는 사이트 루트에 있는 <code class="code-inline">_*collection_name*</code> 폴더에 저장된다.
지금은 <code class="code-inline">_authors</code> 폴더에 해당한다.

각 저자별 문서를 생성한다:

<code class="code-inline">_authors/jill.md</code>:

```liquid
---
short_name: jill
name: Jill Smith
position: Chief Editor
---
Jill은 프랑스 남부에 거주하는 열정적인 과일 재배자이다.
```

<code class="code-inline">_authors/ted.md</code>

```liquid
---
short_name: ted
name: Ted Doe
position: Writer
---
Ted는 아기 때부터 과일을 먹어왔다.
```

## Staff page
사이트에 저자 목록 페이지를 추가해보자. Jekyll에서는 <code class="code-inline">site.authors</code> 변수로 해당 컬렉션을 사용할 수 있다.

루트 디렉터리에 <code class="code-inline">staff.html</code>을 생성하고, <code class="code-inline">site.authors</code>를 순회(iterate)하여 모든 스태프 정보를 출력한다:

```liquid
---
layout: default
title: Staff
---
{% raw %}<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2>{{ author.name }}</h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>{% endraw %}
```

author.content는 마크다운으로 작성되었으므로 <code class="code-inline">markdownify</code> 필터를 적용해야 한다. 이는 레이아웃에서 {% raw %}{{ content }}{% endraw %}를 이용하여 출력하면 자동으로 적용된다.

메인 내비게이션에서도 이 페이지로 이동할 수 있어야 한다. <code class="code-inline">_data/navigation.yml</code>을 열고 staff 항목을 추가한다:

```yaml
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
- name: Staff
  link: /staff.html
```

## Output a page
컬렉션 문서는 별도의 출력 페이지가 기본적으로 생성되지 않는다.
여기서는 각 저자가 개별 페이지를 가져야 하므로, 컬렉션 설정을 수정해야 한다.

<code class="code-inline">_config.yml</code>을 열고 author 컬렉션 설정에 <code class="code-inline">output: true</code>를 추가한다:

```yaml
collections:
  authors:
    output: true
```

변경 사항을 적용하기 위해 Jekyll 서버를 재시작하라.

이제 <code class="code-inline">author.url</code>로 저자 페이지에 접근할 수 있다.

<code class="code-inline">staff.html</code>에 다음과 같이 링크를 추가한다:

```liquid
---
layout: default
title: Staff
---
{% raw %}<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2><a href="{{ author.url }}">{{ author.name }}</a></h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>{% endraw %}
```

게시글(posts)처럼 저자 페이지 전용 레이아웃을 만들어보자.

<code class="code-inline">_layouts/author.html</code> 파일을 생성하고 다음과 같이 작성한다:

```liquid
---
layout: default
---
{% raw %}<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}{% endraw %}
```

## Front matter defaults
이제 저자 문서들이 <code class="code-inline">author</code> 레이아웃을 사용하도록 설정해야 한다. 이전에 했던 것처럼 각 문서의 Front matter에 설정할 수도 있지만, 같은 작업을 계속 반복해야 해서 번거롭다.

모든 게시글은 post, 저자 문서는 author, 그 외 문서들은 default 레이아웃이 적용되도록 하려면 _config.yml에 [front matter defaults]({% link _apis/jekyll/docs/01/front_matter_defaults.md %})을 설정하면 된다.

```yaml
collections:
  authors:
    output: true

defaults:
  - scope:
      path: ""
      type: "authors"
    values:
      layout: "author"
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
  - scope:
      path: ""
    values:
      layout: "default"
```

이제 페이지와 포스트의 front matter에서 layout 항목을 제거해도 된다. 단, <code class="code-inline">_config.yml</code> 변경 후에는 항상 Jekyll 서버를 재시작해야 한다.

## List author's posts
저자 페이지에 해당 저자가 발행한 게시글 목록을 표시해보자.
이를 위해 저자 문서의 <code class="code-inline">short_name</code>을 게시글의 <code class="code-inline">author</code>와 매칭한다. 이 방법으로 게시글을 저자별로 필터링할 수 있다.

<code class="code-inline">_layouts/author.html</code>에서 필터링된 목록을 순회하여 해당 저자의 게시글을 출력해보자:

```liquid
---
layout: default
---
{% raw %}<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}

<h2>Posts</h2>
<ul>
  {% assign filtered_posts = site.posts | where: 'author', page.short_name %}
  {% for post in filtered_posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>{% endraw %}
```

## Link to authors page
게시글 안에서 저자를 참조하여 저자 페이지와 연결할 수도 있다. <code class="code-inline">_layouts/post.html</code>에서 사용한 것과 유사한 필터링 방식을 적용하면 된다.:

```liquid
---
layout: default
---
{% raw %}<h1>{{ page.title }}</h1>

<p>
  {{ page.date | date_to_string }}
  {% assign author = site.authors | where: 'short_name', page.author | first %}
  {% if author %}
    - <a href="{{ author.url }}">{{ author.name }}</a>
  {% endif %}
</p>

{{ content }}{% endraw %}
```

브라우저에서 [http://localhost:4000](http://localhost:4000)에 접속해 staff 페이지와 게시글 내 저자 링크가 정상적으로 연결되는지 확인한다.

이어지는 마지막 단계에서는 사이트를 다듬고 운영 환경에 배포하는 법을 알아볼 것이다.


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
