---
title: Webrick Options
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
_config.yml에 다음 설정을 추가하면 사용자 지정 헤더를 지정할 수 있다.

```yaml
# 파일: _config.yml
webrick:
  headers:
    My-Header: My-Value
    My-Other-Header: My-Other-Value
```

### Defaults
Jekyll은 기본으로 <code class="code-inline">Content-Type</code>과 <code class="code-inline">Cache-Control</code> 응답 헤더를 제공한다. <code class="code-inline">Content-Type</code>은 제공되는 데이터의 유형에 따라 동적으로 설정되고, code class="code-inline">Cache-Control</code>은 개발 모드에서 Chrome의 강한 캐싱으로 인한 문제를 피하기 위해 캐싱을 비활성화하도록 정적으로 지정된다.
