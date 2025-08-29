---
title: API Project
layout: page           # ← 중요: 컬렉션 기본(api_doc)을 덮어써서 일반 페이지로 렌더
nav_order: -1          # 정렬 경고 방지
permalink: /api/       # 인덱스 주소 고정
---

> API 번역 프로젝트. 프로젝트명을 클릭하면 해당 문서로 이동합니다.

{%- comment -%}
  1) 불리언 true와 문자열 'true' 모두 허용해서 contents 루트만 수집
  2) project_title → topic → title 순으로 표시명 결정
{%- endcomment -%}
{% assign roots_bool = site.apis | where: "is_contents", true %}
{% assign roots_str  = site.apis | where: "is_contents", "true" %}
{% assign roots      = roots_bool | concat: roots_str | uniq %}

{% if roots.size == 0 %}
_아직 등록된 프로젝트가 없습니다. `/ _apis/<프로젝트>/contents.md`를 먼저 만들어 주세요._
{% else %}
<table>
  <thead>
    <tr>
      <th>project</th>
      <th>version</th>
      <th>updated in</th>
      <th>original ref</th>
    </tr>
  </thead>
  <tbody>
  {%- assign roots = roots | sort: "project_title" -%}
  {%- for p in roots -%}
    {%- assign proj_name = p.project_title | default: p.topic | default: p.title -%}
    <tr>
      <td><a href="{{ p.url | relative_url }}">{{ proj_name }}</a></td>
      <td>{{ p.version }}</td>
      <td>{{ p.last_updated }}</td>
      <td>
        {%- if p.source_url -%}
          <a href="{{ p.source_url }}" target="_blank" rel="noopener">ref</a>
        {%- endif -%}
      </td>
    </tr>
  {%- endfor -%}
  </tbody>
</table>
{% endif %}
