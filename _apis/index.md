---
title: API Project
permalink: /api/
layout: page
---

> 번역 기반 API 문서 포트폴리오. 프로젝트명을 클릭하면 해당 문서로 이동합니다.

{% comment %}
- contents 문서(`is_contents: true`)만 대상으로 삼고,
- topic이 비어있는(nil) 항목은 제외(compact) 후 정렬.
{% endcomment %}

{% assign contents_docs = site.apis | where_exp: "d", "d.is_contents == true" %}
{% assign topics = contents_docs | map: "topic" | compact | uniq | sort %}

{% if topics.size == 0 %}
<p><em>아직 등록된 프로젝트가 없습니다. <code>_apis/&lt;프로젝트&gt;/contents.md</code>를 먼저 만들어 주세요.</em></p>
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
    {% for t in topics %}
      {% assign contents = contents_docs | where: "topic", t | first %}
      <tr>
        <td><a href="{{ contents.url | relative_url }}">{{ t }}</a></td>
        <td>{{ contents.version }}</td>
        <td>{{ contents.last_updated }}</td>
        <td>
          {% if contents.source_url %}
            <a href="{{ contents.source_url }}">ref</a>
          {% endif %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
{% endif %}
