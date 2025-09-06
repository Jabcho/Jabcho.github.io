---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 8. Blogging
데이터베이스 없이 블로그를 운영할 수 있을까 궁금할 수 있다. Jekyll에서는 텍스트 파일만으로 블로깅을 할 수 있다.

## Posts
블로그 글은 <code class="code-inline">_posts</code>라는 폴더 안에 저장된다. 파일명은 특별한 규칙을 따른다: 발행일, 제목, 확장자 순으로 작성해야 한다.

첫 게시글로 <code class="code-inline">_posts/2018-08-20-bananas.md</code> 파일을 만들고 다음 내용을 입력해보자:

```liquid
---
layout: post
author: jill
---

A banana is an edible fruit – botanically a berry – produced by several kinds of large herbaceous flowering plants in the genus Musa.

In some countries, bananas used for cooking may be called "plantains",
distinguishing them from dessert bananas. The fruit is variable in size, color, and firmness, but is usually elongated and curved, with soft flesh rich in starch covered with a rind, which may be green, yellow, red, purple, or brown when ripe.
```

이 예제는 이전에 작성했던 <code class="code-inline">about.md</code>와 비슷하지만, author 변수와 다른 종류의 레이아웃을 사용한다는 점이 다르다. <code class="code-inline">author</code>는 사용자 정의 변수(custom variable) 로, 필수는 아니며 <code class="code-inline">creator</code>처럼 임의의 이름을 사용할 수도 있다.

## Layout
현재 <code class="code-inline">post</code> 레이아웃은 존재하지 않으므로, <code class="code-inline">_layouts/post.html</code> 파일을 새로 만들고 아래와 같이 작성한다:

```liquid
---
layout: default
---
{% raw %}<h1>{{ page.title }}</h1>
<p>{{ page.date | date_to_string }} - {{ page.author }}</p>

{{ content }}{% endraw %}
```

이 예시는 레이아웃 상속(Layout Inheritance)을 보여준다. post 레이아웃은 default 레이아웃의 글의 제목(title), 날짜(date), 작성자(author), 본문(content)을 출력한다.

추가로, <code class="code-inline">date_to_string</code> 필터는 날짜를 보기 좋은 형식으로 변환한다.

## List posts
현재는 작성한 블로그 글로 이동(navigate)할 방법이 없다. 일반적으로 블로그에는 모든 글을 나열하는 페이지가 있으며, 지금부터 이를 만들어볼 것이다.

Jekyll에서 모든 글은 <code class="code-inline">site.posts</code> 변수로 접근할 수 있다.

루트 디렉터리에 <code class="code-inline">blog.html</code> 파일을 생성하고 다음 내용을 작성한다:

```liquid
{% raw %}---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>{% endraw %}
```

위 코드에서 주의할 점이 몇 가지 있다:

- <code class="code-inline">post.url</code>값은 Jekyll이 자동으로 지정하며, 이는 글의 출력 경로이다.

- <code class="code-inline">post.title</code>은 파일명에서 추출되며, Front Matter에 title을 지정하여 덮어쓸 수 있다.

- <code class="code-inline">post.excerpt</code>는 기본적으로 본문 첫 번째 문단을 출력한다.

이제 메인 내비게이션에서도 이 페이지로 이동하는 방법을 알아보자. 다음과 같이 <code class="code-inline">_data/navigation.yml</code> 파일에 블로그 페이지로 이동하기 위한 항목을 추가하라:

```YAML
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
```

## More posts
블로그에는 하나의 글만 있지 않다. 몇 개를 더 추가해보자:

<code class="code-inline">_posts/2018-08-21-apples.md</code>:

```liquid
---
layout: post
author: jill
---
An apple is a sweet, edible fruit produced by an apple tree.

Apple trees are cultivated worldwide, and are the most widely grown species in the genus Malus. The tree originated in Central Asia, where its wild ancestor, Malus sieversii, is still found today. Apples have been grown for thousands of years in Asia and Europe, and were brought to North America by European colonists.
```

<code class="code-inline">_posts/2018-08-22-kiwifruit.md</code>:

```liquid
---
layout: post
author: ted
---
Kiwifruit (often abbreviated as kiwi), or Chinese gooseberry is the edible berry of several species of woody vines in the genus Actinidia.

The most common cultivar group of kiwifruit is oval, about the size of a large hen's egg (5–8 cm (2.0–3.1 in) in length and 4.5–5.5 cm (1.8–2.2 in) in diameter). It has a fibrous, dull greenish-brown skin and bright green or golden flesh with rows of tiny, black, edible seeds. The fruit has a soft texture, with a sweet and unique flavor.
```

이제 [http://localhost:4000](http://localhost:4000)에 접속해 블로그 글들을 확인해보라.

다음 단계에서는 작성자(author)별 전용 페이지를 만드는 방법을 다룬다.


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
