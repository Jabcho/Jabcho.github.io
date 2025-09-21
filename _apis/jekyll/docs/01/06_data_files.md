---
title: Step by Step Tutorial
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/01/
nav_order: 1  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.


## 6. Data Files
Jekyll은 <code class="code-inline">_data</code> 디렉터리에 위치한 YAML, JSON, CSV 파일로부터 데이터를 불러올 수 있다. 데이터 파일(Data files)은 콘텐츠를 소스 코드와 분리하여 사이트 유지보수를 더욱 용이하게 만든다.

이번 단계에서는 내비게이션 항목을 데이터 파일에 저장한 뒤, 네비게이션 include 파일에서 이를 반복(iterate) 처리하는 방법을 알아본다.

## Data file usage
[YAML](https://yaml.org/)은 Ruby 생태계에서 흔히 사용되는 데이터 포맷이다. 여기서는 YAML을 사용해 내비게이션 항목들을 배열 형태로 저장할 것이다. 각 항목들은 이름(name)과 링크(link)를 가진다.

내비게이션 항목을 저장할 데이터 파일로 <code class="code-inline">_data/navigation.yml</code> 파일을 생성하고 다음과 같이 작성한다:

```liquid
- name: Home
  link: /
- name: About
  link: /about.html
```

Jekyll에서는 이 데이터 파일을 <code class="code-inline">site.data.navigation</code> 객체로 접근할 수 있다. 이제 <code class="code-inline">_includes/navigation.html</code>에서 각 링크를 직접 하나씩 작성해 출력하는 대신, 데이터 파일을 반복 처리하여 출력할 수 있다:

```liquid
{% raw %}<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}{% endraw %}
</nav>
```

출력 결과는 이전과 동일하다. 하지만 이제 새로운 내비게이션 항목을 추가하거나 HTML 구조를 변경하는 작업이 훨씬 간단해졌다.

웹사이트는 CSS, JavaScript, 이미지를 필요로 한다. 이제 Jekyll에서 자산(assets)을 다루는 방법을 알아보자.


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
