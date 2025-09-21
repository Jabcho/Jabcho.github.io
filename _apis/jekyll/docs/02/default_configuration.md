---
title: Default Configuration
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
Jekyll은 기본적으로 다음 설정 옵션에 따라 동작한다. 이 옵션들은 설정 파일이나 명령줄에서 직접 지정할 수 있다.
<br>
<div class="blue-caution">
ℹ️ **디렉터리 경로 주의**

일반적으로 <code class="code-inline">plugins_dir</code> 같은 설정 키의 디렉터리 경로 값은 사이트 소스가 아닌 현재 작업 디렉터리 기준 상대 경로를 사용한다. 예외적으로 <code class="code-inline">sass</code> 설정 키의 값은 사이트 소스 기준 상대 경로를 사용한다.
</div>
<br>

```yaml
# 위치(Where things are)
source              : .
destination         : ./_site
collections_dir     : .
plugins_dir         : _plugins # 문자열 배열 순서대로 플러그인을 로드
layouts_dir         : _layouts
data_dir            : _data
includes_dir        : _includes
sass:
  sass_dir: _sass
collections:
  posts:
    output          : true

# 읽기 처리(Handling Reading)
safe                : false
include             : [".htaccess"]
exclude             : ["Gemfile", "Gemfile.lock", "node_modules", "vendor/bundle/", "vendor/cache/", "vendor/gems/", "vendor/ruby/"]
keep_files          : [".git", ".svn"]
encoding            : "utf-8"
markdown_ext        : "markdown,mkdown,mkdn,mkd,md"
strict_front_matter : false

# 콘텐츠 필터링(Filtering Content)
show_drafts         : null
limit_posts         : 0
future              : false
unpublished         : false

# 플러그인(Plugins)
whitelist           : []
plugins             : []

# 변환(Conversion)
markdown            : kramdown
highlighter         : rouge
lsi                 : false
excerpt_separator   : "\n\n"
incremental         : false

# 서비스(Serving)
detach              : false
port                : 4000
host                : 127.0.0.1
baseurl             : "" # 호스트명은 포함하지 않음
show_dir_listing    : false

# 출력(Outputting)
permalink           : date
paginate_path       : /page:num
timezone            : null

quiet               : false
verbose             : false
defaults            : []

liquid:
  error_mode        : warn
  strict_filters    : false
  strict_variables  : false

# 마크다운 프로세서(Markdown Processors)
kramdown:
  auto_ids          : true
  entity_output     : as_char
  toc_levels        : [1, 2, 3, 4, 5, 6]
  smart_quotes      : lsquo,rsquo,ldquo,rdquo
  input             : GFM
  hard_wrap         : false
  footnote_nr       : 1
  show_warnings     : false
  ```
