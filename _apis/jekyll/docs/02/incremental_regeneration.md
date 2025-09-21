---
title: Incremental Regeneration
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---


> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
<div class="red-caution">
⚠️ 증분 재생성(Incremental regeneration)은 아직 실험 단계에 있다
증분 재생성은 일반적인 경우에는 동작하지만, 모든 시나리오에서 올바르게 동작하는 것은 아니다. 따라서 이 기능을 사용할 때는 각별한 주의가 필요하며, 아래에서 다뤄지지 않은 문제는 [깃허브 이슈](https://github.com/jekyll/jekyll/issues/new)를 열어서 보고해주기 바란다.
</div>

증분 재생성은 이전 빌드 이후에 변경된 문서와 페이지만 재생성하여 빌드 시간을 단축한다. 이를 위해 <code class="code-inline">.jekyll-metadata</code> 파일에 파일 수정 시각과 문서 간 의존성을 함께 기록해 추적한다.

현재는 문서나 페이지 자체가 수정되었거나, 그 문서의 의존성이 수정된 경우에만 증분 재생성을 실행한다. 현재 추적 가능한 의존성 유형은 includes({% raw %}{% include %}{% endraw %} 태그 사용)와 layouts뿐이다. 따라서 단순히 다른 문서를 참조하는 경우(예를 들어, 게시글 목록 페이지에서 <code class="code-inline">site.posts</code>를 순회하는 일반적인 경우)는 의존성으로 감지되지 않는다.

이 한계를 보완하기 위해, 문서의 Front matter에 <code class="code-inline">regenerate: true</code>를 설정하면 수정 여부와 관계없이 Jekyll이 해당 문서를 재생성한다. 단, 다른 문서의 내용을 참조하는 부분은 그 문서들이 재렌더링되는 것이 아니므로 재생성되지 않는다는 점에 유의하라.

증분 재생성은 명령줄에서 <code class="code-inline">--incremental</code> 플래그(축약형 <code class="code-inline">-I</code>)를 사용하거나, 설정 파일에 <code class="code-inline">incremental: true</code>를 지정하여 활성화할 수 있다.

