---
layout: page
title: Home
permalink: /

---

<div class="home-intro">
  <p>Jabcho's API 번역 프로젝트(+α) 블로그</p>
</div>

<div class="home-cards">
  <a class="home-card" href="{{ '/blog/' | relative_url }}">
    <h2>BLOG</h2>
  </a>
  <a class="home-card" href="{{ '/api/' | relative_url }}">
    <h2>API Project</h2>
  </a>
</div>

<style>
  /* 홈(/)에서만 로드되는 스타일: HOME 항목을 하이라이트처럼 표시 */
  #sidebar a.nav-link[href="{{ '/' | relative_url }}"] {
    font-weight: 700;
    background: rgba(0,0,0,.06);    /* 필요하면 수치 조정 */
    border-radius: 12px;
  }
  #sidebar a.nav-link[href="{{ '/' | relative_url }}"] i { color: inherit; }
</style>
