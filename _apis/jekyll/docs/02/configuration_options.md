---
title: Configuration Options
project_id: jekyll   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/jekyll/02/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
아래 표는 Jekyll에서 사용 가능한 설정과, 해당 설정을 제어하는 다양한 옵션(구성 파일에 지정)과 플래그(명령줄에 지정)를 나열한다.

### Global Configuration

<!-- th(헤더)만 가운데 정렬로 변경 -->
<style>
.wrap-table{width:100%;table-layout:fixed;border-collapse:collapse}
.wrap-table th,.wrap-table td{padding:6px 8px;vertical-align:top;border:1px solid #e5e7eb}
.wrap-table th,.wrap-table td{white-space:normal !important;overflow-wrap:anywhere !important;word-break:break-word !important}
.wrap-table code,.wrap-table kbd,.wrap-table samp{white-space:normal !important;overflow-wrap:anywhere !important;word-break:break-all !important}
/* 두 번째 열(td)은 가운데 정렬 유지 */
.wrap-table th:nth-child(2), .wrap-table td:nth-child(2){text-align:center}
/* ★ 헤더 행(th) 전체를 가운데 정렬 */
.wrap-table thead th{text-align:center}
/* 버전 노란색 배경 표기 */
.ver-badge{
  display:inline-block;
  padding:.12em .55em;
  font-size:.75em;        /* 본문보다 약간 작게 */
  font-weight:700;
  line-height:1.6;
  color:#1f2937;          /* 어두운 회색 글자 */
  background:#facc15;     /* 노란 배경(amber-400 계열) */
  border:1px solid #eab308;
  border-radius:.5em;     /* 둥근 모서리(알약 모양) */
  vertical-align:middle;
  white-space:nowrap;     /* 숫자가 줄바꿈되지 않게 */
}
</style>

<table class="wrap-table">
  <colgroup>
    <col style="width:64%">
    <col style="width:36%">
  </colgroup>
  <thead>
    <tr>
      <th>설정</th>
      <th>옵션 · 플래그</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>사이트 소스(Site source)</strong><br>Jekyll이 파일을 읽을 디렉터리를 변경.</td>
      <td><code class="code-inline">source: DIR</code><br><code class="code-inline">-s, --source DIR</code></td>
    </tr>
    <tr>
      <td><strong>사이트 출력 위치(Site destination)</strong><br>Jekyll이 파일을 쓸 디렉터리를 변경.</td>
      <td><code class="code-inline">destination: DIR</code><br><code class="code-inline">-d, --destination DIR</code></td>
    </tr>
    <tr>
      <td><strong>안전 모드(Safe)</strong><br><a href="#">허용 목록 외 플러그인</a> 및 디스크 캐시 비활성화, 심볼릭 링크 무시.</td>
      <td><code class="code-inline">safe: BOOL</code><br><code class="code-inline">--safe</code></td>
    </tr>
    <tr>
      <td><strong>디스크 캐시 비활성화  <span class="ver-badge">4.1.0</span></strong><br>소스에 <code class="code-inline">.jekyll-cache</code> 등 캐시 디렉터리가 생성되지 않도록 디스크 캐싱(caching)을 비활성화하여 가상환경이나 외부 감시 도구와의 간섭을 방지한다. 안전 모드에서는 항상 비활성화 상태이다.</td>
      <td><code class="code-inline">disable_disk_cache: BOOL</code><br><code class="code-inline">--disable-disk-cache</code></td>
    </tr>
    <tr>
      <td><strong>테마 설정 무시 <span class="ver-badge">4.1.0</span></strong><br>Jekyll 4.0부터는 신규 사용자도 테마를 쉽게 사용할 수 있도록 각 테마 내부에 <code class="code-inline">_config.yml</code>를 포함하여 제공할 수 있다. 만약 테마에 포함된 설정을 가져오면서 병합된 최종 설정이 엉키는 문제가 생긴다면, Jekyll이 테마 설정을 불러오지 않도록 설정할 수 있다.</td>
      <td><code class="code-inline">ignore_theme_config: BOOL</code></td>
    </tr>
    <tr>
      <td><strong>제외(Exclude)</strong><br>변환될 때 특정 디렉터리나 파일을 제외한다. 이 때 경로는 소스 기준 상대경로만 가능하며, 소스 외부 경로는 사용 불가하다.<br>이 설정 옵션은 Ruby의 <code class="code-inline">File.fnmatch</code> 방식의 파일명 글로브 패턴을 지원하여 여러 개의 제외 항목을 한번에 매칭할 수 있다. 예를 들어, 다음과 같이 <code class="code-inline">exclude</code> 옵션을 설정함으로서 소스 트리에 있는 README.md 파일들을 사이트에서 제외할 수 있다: <code class="code-inline">["README.md","**/README.md"]</code><br> 
      Jekyll 3에서는 <code class="code-inline">exclude</code> 설정이 기본 제외 항목을 대체한다. Jekyll 4에서는 사용자가 지정한 항목들이 기본 제외 항목에 추가되며, 기본 설정을 무시하려면 <code class="code-inline">include</code> 옵션을 사용한다.<br>
      기본 제외 항목들은 <code class="code-inline">jekyll new</code>에 의해 생성된 <code class="code-inline">_config.yml</code> 파일에서 확인할 수 있다:<br> 
      <ul>
      <li><code class="code-inline">/.sass-cache/</code></li>
      <li><code class="code-inline">/.jekyll-cache/</code></li>
      <li><code class="code-inline">/gemfiles/</code></li>
      <li><code class="code-inline">Gemfile</code></li>
      <li><code class="code-inline">Gemfile.lock</code></li>
      <li><code class="code-inline">/node_modules/</code></li>
      <li><code class="code-inline">/vendor/bundle/</code></li>
      <li><code class="code-inline">/vendor/cache/</code></li>
      <li><code class="code-inline">/vendor/gems/</code></li>
      <li><code class="code-inline">/vendor/ruby/</code></li></ul></td>
      <td><code class="code-inline">exclude: [DIR, FILE, ...]</code></td>
    </tr>
    <tr>
      <td><strong>포함(Include)</strong><br>
      변환 과정에서 특정 디렉터리나 파일을 강제로 포함시킨다. 점 파일은 기본적으로 제외되므로 <code class="code-inline">.htaccess</code> 같은 파일을 포함하려면 이 옵션에 추가할 수 있다.<br>
      이 설정 옵션은 Ruby의 <code class="code-inline">File.fnmatch</code> 방식의 파일명 글로브 패턴을 지원하므로 여러 항목을 한번에 포함 대상으로 매칭할 수 있다. 보다 자세한 설명은 <code class="code-inline">exclude</code>를 참고하라.<br>
      Jekyll 4에서는 <code class="code-inline">include</code>가 <code class="code-inline">exclude</code>설정보다 우선 적용된다.</td>
      <td><code class="code-inline">include: [DIR, FILE, ...]</code></td>
    </tr>
    <tr>
      <td><strong>파일 보존(Keep files)</strong><br>
      사이트 출력 폴더 정리 시 지정 파일된 파일을 보존한다. 빌드 도구가 만든 파일이나 자산 등 Jekyll이 생성하지 않은 파일들을 보존할 때 유용하다. 이 때 경로는 출력 폴더를 기준으로 한 상대경로이다.</td>
      <td><code class="code-inline">keep_files: [DIR, FILE, ...]</code></td>
    </tr>
    <tr>
      <td><strong>시간대(Time zone)</strong><br>
      사이트 생성에 사용할 시간대를 설정한다. <code class="code-inline">TZ</code> 환경 변수를 설정하면 Ruby는 이를 이용하여 날짜와 시간을 생성하고 조작한다. IANA 시간대 데이터베이스(IANA Time Zone Database)에 있는 항목이면 무엇이든 유효하다(예: <code class="code-inline">America/New_York</code>). 전체 목록은 <a href="https://en.wikipedia.org/wiki/List_of_tz_database_time_zones">여기</a>에서 확인할 수 있다.
      로컬 환경에서 서버를 실행할 경우 기본 시간대는 사용하는 운영체제 설정을 따르며, 원격 호스트나 서버에서 실행할 경우 해당 서비스의 설정이나 위치에 따른다.</td>
      <td><code class="code-inline">timezone: TIMEZONE</code></td>
    </tr>
    <tr>
      <td><strong>인코딩(Encoding)</strong><br>
      파일 인코딩을 이름으로 설정한다(Ruby 1.9 이상에서만 제공됨). 기본값은 Ruby 2.0.0부터 <code class="code-inline">utf-8</code>dlau, 2.0.0 이전은 <code class="code-inline">nil</code>로서 Ruby의 기본값인 <code class="code-inline">ASCII-8BIT</code>가 적용된다. 사용 가능한 인코딩은 다음 명령어로 확인할 수 있다: <code class="code-inline">ruby -e 'puts Encoding::list.join("\n")'</code></td>
      <td><code class="code-inline">encoding: ENCODING</code></td>
    </tr>
    <tr>
      <td><strong>기본값 (Defaults)</strong><br>
      <a href="#">Front Matter</a> 변수의 기본값을 설정한다.</td>
      <td><a href="./front_matter_defaults.md">아래</a> 참조</td>
    </tr>
  </tbody>
</table>

<div class="red-caution">
⚠️ <strong>사이트 빌드 시 출력 폴더(Destination folders) 정리</strong><br><br>
기본적으로 사이트를 빌드하면 <code class="code-inline">&lt;destination&gt;</code>의 내용은 자동으로 정리된다. 사이트에서 생성하지 않은 파일이나 폴더들은 제거된다. 필요한 파일은 <code class="code-inline">&lt;keep_files&gt;</code> 설정 항목으로 지정하여 보존할 수 있다.
<code class="code-inline">&lt;destination&gt;</code>에는 중요한 위치를 사용하지 말아야 하며, 보관(staging) 용도로만 사용한 후 파일을 웹 서버 디렉터리로 복사하는 것을 권장한다.
</div>

<br>

### Build Command Options

<style>
.wrap-table{width:100%;table-layout:fixed;border-collapse:collapse}
.wrap-table th,.wrap-table td{padding:6px 8px;vertical-align:top;border:1px solid #e5e7eb}
.wrap-table th,.wrap-table td{white-space:normal !important;overflow-wrap:anywhere !important;word-break:break-word !important}
.wrap-table code,.wrap-table kbd,.wrap-table samp{white-space:normal !important;overflow-wrap:anywhere !important;word-break:break-all !important}
/* 두 번째 열(td)은 가운데 정렬 유지 */
.wrap-table th:nth-child(2), .wrap-table td:nth-child(2){text-align:center}
/* ★ 헤더 행(th) 전체를 가운데 정렬 */
.wrap-table thead th{text-align:center}
</style>

<table class="wrap-table">
  <colgroup>
    <col style="width:64%">
    <col style="width:36%">
  </colgroup>
  <thead>
    <tr>
      <th>설정</th>
      <th>옵션 · 플래그</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><strong>재생성(Regeneration)</strong><br>
    파일 변경 시 사이트가 자동으로 재생성된다.</td><td><code class="code-inline">-w, --[no-]watch</code></td></tr>
    <tr><td><strong>설정(Configuration)</strong><br>기본 <code class="code-inline">_config.yml</code> 대신 사용할 설정 파일을 지정한다. 후에 지정한 파일의 설정이 앞선 파일의 설정을 덮어쓴다.</td><td><code class="code-inline">--config FILE1[,FILE2,...]</code></td></tr>
    <tr><td><strong>플러그인(Plugins)</strong><br>기본 <code class="code-inline">_plugins/</code> 대신 사용할 플러그인 디렉터리을 지정한다.</td><td><code class="code-inline">plugins_dir: [DIR1,...]</code><br><code class="code-inline">-p, --plugins DIR1[,DIR2,...]</code></td></tr>
    <tr><td><strong>레이아웃(Layouts)</strong><br>기본 <code class="code-inline">_layouts/</code> 대신 사용할 레이아웃 디렉터리 지정.</td><td><code class="code-inline">layouts_dir: DIR</code><br><code class="code-inline">--layouts DIR</code></td></tr>
    <tr><td><strong>초안(Drafts)</strong><br>게시글 초안을 처리하고 렌더링한다.</td><td><code class="code-inline">show_drafts: BOOL</code><br><code class="code-inline">-D, --drafts</code></td></tr>
    <tr><td><strong>환경(Environment)</strong><br>빌드 시 환경 값을 직접 지정한다.</td><td><code class="code-inline">JEKYLL_ENV=production</code></td></tr>
    <tr><td><strong>미래 게시물(Future)</strong><br>미래 날짜가 지정된 게시글이나 컬렉션 문서를 게시한다.</td><td><code class="code-inline">future: BOOL</code><br><code class="code-inline">--future</code></td></tr>
    <tr><td><strong>비공개(Unpublished)</strong><br>비공개로 처리된 게시글을 렌더링한다.</td><td><code class="code-inline">unpublished: BOOL</code><br><code class="code-inline">--unpublished</code></td></tr>
    <tr><td><strong>LSI</strong><br>관련 게시글의 색인을 생성한다.(<code class="code-inline"><a href="https://jekyll.github.io/classifier-reborn/">classifier-reborn</a></code> 플러그인 필요).</td><td><code class="code-inline">lsi: BOOL</code><br><code class="code-inline">--lsi</code></td></tr>
    <tr><td><strong>게시물 제한(Limit posts)</strong><br>파싱·게시할 게시글 수를 제한한다.</td><td><code class="code-inline">limit_posts: NUM</code><br><code class="code-inline">--limit_posts NUM</code></td></tr>
    <tr><td><strong>강제 폴링(Force polling)</strong><br>watch가 폴링(polling) 방식을 사용하도록 강제한다.</td><td><code class="code-inline">force_polling: BOOL</code><br><code class="code-inline">--force_polling</code></td></tr>
    <tr><td><strong>자세한 출력 (Verbose)</strong><br>상세 로그 출력.</td><td><code class="code-inline">verbose: BOOL</code><br><code class="code-inline">-V, --verbose</code></td></tr>
    <tr><td><strong>정숙 출력 (Quiet)</strong><br>일반 출력 억제.</td><td><code class="code-inline">quiet: BOOL</code><br><code class="code-inline">-q, --quiet</code></td></tr>
    <tr><td><strong>로그 레벨 (Log level)</strong><br><code class="code-inline">debug</code> · <code class="code-inline">info</code> · <code class="code-inline">warn</code> · <code class="code-inline">error</code> 중 지정.</td><td><code class="code-inline">JEKYLL_LOG_LEVEL=info</code></td></tr>
    <tr><td><strong>증분 빌드 (Incremental build)</strong><br>변경된 항목만 재빌드(실험적).</td><td><code class="code-inline">incremental: BOOL</code><br><code class="code-inline">-I, --incremental</code></td></tr>
    <tr><td><strong>Bundler require 비활성화</strong><br>Gemfile <code class="code-inline">:jekyll_plugins</code>에서 <code class="code-inline">require</code> 생략.</td><td><code class="code-inline">JEKYLL_NO_BUNDLER_REQUIRE=true</code></td></tr>
    <tr><td><strong>Liquid 프로파일러</strong><br>Liquid 렌더링 프로파일 생성.</td><td><code class="code-inline">profile: BOOL</code><br><code class="code-inline">--profile</code></td></tr>
    <tr><td><strong>엄격한 프런트 매터</strong><br>프런트 매터 YAML 오류 시 빌드 실패.</td><td><code class="code-inline">strict_front_matter: BOOL</code><br><code class="code-inline">--strict_front_matter</code></td></tr>
    <tr><td><strong>웹 도메인 URL (Web Domain URL)</strong><br>프로덕션 루트의 정규 URL. 끝에 슬래시 금지. <code class="code-inline">absolute_url</code> 사용 시 <code class="code-inline">baseurl</code>과 결합. <code class="code-inline">jekyll serve</code> 실행 시 <code class="code-inline">localhost</code>로 자동 설정.</td><td><code class="code-inline">url: SCHEME://HOST[:PORT]</code></td></tr>
    <tr><td><strong>기본 경로 (Base URL)</strong><br>도메인 루트와 랜딩 페이지 사이 하위 경로.</td><td><code class="code-inline">baseurl: /PATH/TO/SITE</code><br><code class="code-inline">-b, --baseurl /PATH/TO/SITE</code></td></tr>
    <tr><td><strong>추적 (Trace)</strong><br>에러 발생 시 전체 백트레이스 출력.</td><td><code class="code-inline">-t, --trace</code></td></tr>
  </tbody>
</table>

### Serve Command Options

<style>
.wrap-table{width:100%;table-layout:fixed;border-collapse:collapse}
.wrap-table th,.wrap-table td{padding:6px 8px;vertical-align:top;border:1px solid #e5e7eb}
.wrap-table th,.wrap-table td{white-space:normal !important;overflow-wrap:anywhere !important;word-break:break-word !important}
.wrap-table code,.wrap-table kbd,.wrap-table samp{white-space:normal !important;overflow-wrap:anywhere !important;word-break:break-all !important}
/* 두 번째 열(td)은 가운데 정렬 유지 */
.wrap-table th:nth-child(2), .wrap-table td:nth-child(2){text-align:center}
/* ★ 헤더 행(th) 전체를 가운데 정렬 */
.wrap-table thead th{text-align:center}
</style>

<table class="wrap-table">
  <colgroup>
    <col style="width:64%">
    <col style="width:36%">
  </colgroup>
  <thead>
    <tr>
      <th>설정</th>
      <th>옵션 · 플래그</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><strong>로컬 서버 포트</strong><br>지정 포트로 리슨(기본 4000).</td><td><code class="code-inline">port: PORT</code><br><code class="code-inline">-P, --port PORT</code></td></tr>
    <tr><td><strong>로컬 서버 호스트명</strong><br>지정 호스트명으로 리슨(기본 localhost).</td><td><code class="code-inline">host: HOSTNAME</code><br><code class="code-inline">-H, --host HOSTNAME</code></td></tr>
    <tr><td><strong>라이브 리로드</strong><br>콘텐츠 변경 시 브라우저 자동 새로고침.</td><td><code class="code-inline">livereload: BOOL</code><br><code class="code-inline">-l, --livereload</code></td></tr>
    <tr><td><strong>라이브 리로드 무시</strong><br>무시할 글로브 패턴. CLI 전달 시 인용(따옴표) 권장. 패턴은 <code class="code-inline">relative_path</code> 기준. 필요 시 구성 파일에 나열.</td><td><code class="code-inline">livereload_ignore: [GLOB1,...]</code><br><code class="code-inline">--livereload-ignore GLOB1[,GLOB2,...]</code></td></tr>
    <tr><td><strong>라이브 리로드 지연</strong><br>자동 새로고침 최소/최대 지연(초).</td><td><code class="code-inline">livereload_min_delay: SECONDS</code><br><code class="code-inline">livereload_max_delay: SECONDS</code><br><code class="code-inline">--livereload-min-delay SECONDS</code><br><code class="code-inline">--livereload-max-delay SECONDS</code></td></tr>
    <tr><td><strong>라이브 리로드 포트</strong><br>LiveReload 포트(4.4.0부터 구성 파일로 재정의 가능).</td><td><code class="code-inline">livereload_port: PORT</code><br><code class="code-inline">--livereload-port PORT</code></td></tr>
    <tr><td><strong>URL 열기</strong><br>서버 시작 시 사이트 URL을 브라우저에서 열기.</td><td><code class="code-inline">open_url: BOOL</code><br><code class="code-inline">-o, --open-url</code></td></tr>
    <tr><td><strong>분리 실행 (Detach)</strong><br>서버를 터미널에서 분리.</td><td><code class="code-inline">detach: BOOL</code><br><code class="code-inline">-B, --detach</code></td></tr>
    <tr><td><strong>초기 빌드 건너뛰기</strong><br>서버 시작 전 초기 빌드 생략.</td><td><code class="code-inline">skip_initial_build: BOOL</code><br><code class="code-inline">--skip-initial-build</code></td></tr>
    <tr><td><strong>디렉터리 목록 표시</strong><br>인덱스 대신 디렉터리 목록 노출.</td><td><code class="code-inline">show_dir_listing: BOOL</code><br><code class="code-inline">--show-dir-listing</code></td></tr>
    <tr><td><strong>X.509(SSL) 개인 키</strong><br>사이트 소스에 저장/심볼릭 링크된 개인 키 경로.</td><td><code class="code-inline">--ssl-key</code></td></tr>
    <tr><td><strong>X.509(SSL) 인증서</strong><br>사이트 소스에 저장/심볼릭 링크된 공개 인증서 경로.</td><td><code class="code-inline">--ssl-cert</code></td></tr>
  </tbody>
</table>

구성 파일에서 탭 사용 금지

구성 파일에 탭 문자를 사용하면 파싱 오류가 발생하거나 기본 설정으로 되돌아갈 수 있다.  
반드시 **스페이스**를 사용할 것.
