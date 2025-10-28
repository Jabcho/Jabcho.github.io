---
title: Navigating Postman
project_id: postman   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/postman/02/02_basics/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
Postman에는 API 프로젝트를 관리할 수 있도록 도와주는 다양한 도구, 보기, 그리고 제어 기능이 있습니다.
이 가이드는 Postman의 주요 인터페이스 영역에 대한 전반적인 개요를 소개합니다:

- [헤더(Header)](#header)
  
- [사이드바(Sidebar)](#sidebar)

- [워크벤치(Workbench)](#workbench)
  - [탭(Tabs)](#tabs)
  - [오른쪽 사이드바(Right sidebar)](#right-sidebar)
  - [환경 선택기 및 변수 창(Environment selector and  variables pane)](#environment-selector-and-variables-pane)
  - [빠른 도움말(Quick Help)](#quick-help)

- [푸터(Footer)]

![navigating_postman]({{ '/assets/img/02/02_basics/navigating_postman.png' | relative_url }})

## Header
헤더(Header)를 통해 워크스페이스 생성, 리포트 확인, Postman API 네트워크 탐색, Postman 내 검색, 동기화 상태 및 알림 확인, 설정, 계정, [Postman 플랜]({% link _apis/postman/01.md %}#billing)에 접근할 수 있습니다.

🔹 기본 기능

- **← →** - ([Postman 데스크톱] 앱 전용)
Postman에서 이전 또는 다음 페이지로 이동합니다.
![header]({{ '/assets/img/02/02_basics/header.png' | relative_url }})

- **Home** - 개인 홈 화면으로 이동합니다. 최근에 방문한 워크스페이스 목록과, 팀이 있을 경우 [팀]({% link _apis/postman/08.md %}#team-management) 리소스로 연결되는 링크가 포함되어 있습니다.

- **Workspaces** - 워크스페이스를 검색하거나, 최근에 방문한 워크스페이스를 확인하거나, [새 워크스페이스를 만들]({% link _apis/postman/06.md %}) 수 있습니다.

- **API Network** - [Postman API 네트워크]({% link _apis/postman/docs/02/01_first/explore_the_postman_api_network.md %})를 탐색할 수 있습니다.

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.search-postman-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.search-postman-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-search-postman.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

- <span class="search-postman-icon"></span> **Search Postman** - Postman 내의 모든 워크스페이스, 컬렉션, 요청(Request), API, 플로우(Flows), 팀을 검색할 수 있습니다. Postman 검색에 대한 자세한 내용은 [Postman에서 검색하기](#search-postman)
를 참고하세요.

![header_search_postman]({{ '/assets/img/02/02_basics/header_search_postman.png' | relative_url }})

- **Invite** - 워크스페이스의 [Admin 권한]({% link _apis/postman/docs/08/01.5_roles/roles_and_permissions.md %}#workspace-roles)을 가진 경우, 다른 사용자를 초대하여 협업할 수 있습니다.

![header_invite]({{ '/assets/img/02/02_basics/header_invite.png' | relative_url }})

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.settings-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.settings-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-settings.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

- <span class="settings-icon"></span> **Settings** - [Postman 설정]({% link _apis/postman/docs/02/04_install/settings.md %}) 및 기타 리소스에 접근합니다.

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.notifications-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.notifications-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-notifications.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

- <span class="notifications-icon"></span> Notifications - 팀의 최근 활동, Postman 업데이트 알림, 풀 리퀘스트(Pull Request), 댓글 활동 등 중요한 정보들을 확인할 수 있습니다.

- **Your avatar** - 프로필 보기, [계정 및 알림 설정]({% link _apis/postman/docs/02/03_account/manage_postman_settings.md %}), 현재 로그인 중인 세션 확인, 계정 로그아웃 등을 할 수 있습니다.

- **Team (유료 플랜) / Upgrade (무료 플랜)** - [리소스 사용량]({% link _apis/postman/docs/08/04_billing/about_resource_usage.md %})을 확인하고, [결제 대시보드]({% link _apis/postman/docs/08/04_billing/manage_billing.md %}) 및 기타 계정 관리 도구에 접근할 수 있습니다.

### Search Postman
Postman에서 원하는 항목을 검색하려면 다음 단계를 따르세요:

1. 헤더에서 **Search Postman**을 클릭하고 검색어를 입력합니다. 또한 **⌘+K**(macOS) 또는 **Ctrl+K**(Windows/Linux) 단축키를 사용할 수 있습니다.

2. 워크스페이스 유형별로 검색 범위를 설정할 수 있습니다. 검색창 아래의 **Workspace** 드롭다운을 클릭하고 **Internal**, **Partner**, **Public** 중 하나를 선택하면 검색할 워크스페이스 범위를 설정할 수 있습니다.

3. 선택한 워크스페이스 타입 내에서 요소(Element) 유형별로 검색할 수 있습니다. **Element type** 드롭다운을 클릭하고 **Workspaces**, **Collections**, **API**, **Request**, **Folder**, **Publisher** 중 하나를 선택하세요. 표시되는 **요소 항목**은 선택한 워크스페이스 유형에 따라 달라집니다.

4. **Workspace type**과 **Element type** 드롭다운 아래의 옵션을 선택하면 현재 작업 중인 워크스페이스나 컬렉션 내에서만 검색할 수도 있습니다. **Search Postman**을 클릭하면 현재 작업중인 워크스페이스가 기본값으로 표시됩니다.
특정 컬렉션에서 작업중이라면 현재 워크스페이스와 해당 컬렉션 모두 기본값으로 표시됩니다.
또는 검색할 때 "in:" 키워드를 사용해 현재 작업중인 워크스페이스나 컬렉션으로 검색 범위를 한정할 수 있습니다.

[Private API Network]({% link _apis/postman/docs/06/11_private/explore_your_private_api_network.md %})
에서 API를 검색하려면
**Workspace** 드롭다운에서 **Internal**, **Element type** 드롭다운에서 **API**를 선택합니다.
반대로 [Postman API Network(공개 API 네트워크)]({% link _apis/postman/12.md %})를 검색하려면 **Workspace** 드롭다운에서 **Public**을 선택한 후 **Element type** 드롭다운에서 **API**를 선택하세요.

팀 멤버가 컬렉션, API, 워크스페이스에 추가한 태그(tag)명으로 검색할 수 있습니다(Enterprise 플랜 전용). 태그명으로 검색하려면 헤더의 **Search Postman**을 클릭하고 "tag:_태그이름_" 형식으로 입력합니다. 예를 들어 API에 production 태그가 있다면 "tag:production"을 입력해서 해당 API를 검색할 수 있습니다.

<div style="
  border:1px solid #EDEDED;
  background: #F9F9F9;
  border-radius:14px;
  padding:18px 22px;
  display:flex; align-items:center; justify-content:space-between; gap:16px;
  box-shadow:0 2px 0 rgba(33,150,243,.08);
">
  <div style="display:flex; align-items:center; gap:12px;">
    <div style="line-height:1.35;">
        로그인하지 않은 사용자는 공개 리소스(public resources)만 검색할 수 있습니다.
    </div>
  </div>
</div>

결과 목록에서 원하는 항목을 찾지 못했다면 **View all results**를 클릭해 전체 결과를 한 페이지에서 확인하세요.

요소(Element) 타입에 따라 검색 결과에 표시되는 정보가 달라질 수 있습니다:

- _워크스페이스(Workspaces)_의 경우, 검색 결과에는 워크스페이스 유형, 요약(Summary), 게시자, 게시 시간이 표시됩니다.

- _컬렉션(Collections)_의 경우, 검색 결과에는 워크스페이스 유형, 컬렉션의 포크(Fork) 여부, 게시자, 게시 시간이 표시됩니다.

- _API_의 경우, 검색 결과에는 API 이름과 요약, API 소유자(개인 사용자 또는 팀), 워크스페이스 유형이 표시됩니다.

- _팀(Teams)_의 경우, 검색 결과에는 팀 이름과 요약이 표시됩니다. 팀 이름을 클릭하면 해당 팀의 프로필 페이지로 이동합니다.

## Sidebar
Postman의 사이드바에서는 [Postman의 기본 구성 요소]({% link _apis/postman/docs/02/02_basics/postman_elements.md %})에 접근할 수 있습니다.

각 구성 요소들은 더 많은 작업을 선택할 수 있는 옵션을 제공합니다. 사이드바에서 요소를 클릭하고 항목 위에 마우스를 올리면 **더보기** 아이콘(⋯) 이 표시됩니다. 표시되는 옵션은 요소 유형에 따라 달라집니다.

컬렉션과 사용 이력(History) 내 여러 개의 컬렉션, 폴더, 요청(request)을 한꺼번에 삭제하거나 이동하려면 ⌘(Mac) 또는 Ctrl(Windows) 키를 누른 상태에서 항목들을 선택합니다.

컬렉션 및 그 안의 콘텐츠에 대한 복사(Copy), 붙여넣기(Paste), 삭제(Delete) 등의 작업은 [키보드 단축키]({% link _apis/postman/docs/02/04_install/settings.md %}#shortcuts)로도 수행할 수 있습니다.

요청(request), 워크스페이스(workspace) 등
Postman 요소를 새로 만들려면 워크스페이스 이름 옆의 **New** 를 클릭하세요. 자주 사용하는 요소는 고정(Pin) 할 수도 있습니다. 요소를 고정하려면 요소 위에 마우스를 올리고 핀 아이콘(📌)을 클릭하세요. 고정된 요소의 핀 아이콘을 다시 클릭하면 고정이 해제됩니다.

![sidebar]({{ '/assets/img/02/02_basics/sidebar.png' | relative_url }})

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.collapse-sidebar-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.collapse-sidebar::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-collapse-sidebar.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

사이드바를 숨기려면 [하단(footer)]의 Collapse sidebar 아이콘(<span class="collapse-sidebar-icon"></span>) 을 클릭하거나, 사이드바의 빈 공간을 우클릭한 뒤 Collapse sidebar를 클릭하세요. 또한 사이드바를 우클릭해서 라벨을 표시하거나 숨길 수 있으며, 사이드바를 접거나 구성을 변경할 수도 있습니다.

### Add elements to the sidebar
### History
### Clearing your history
### Saving responses in history

## Workbench

### Tabs
### Opening a new tab
### Saving or discarding changes
### Renaming and linking elements
### Viewing conflicts
### Managing tabs
### Tab search
### Browser tabs in the Postman web app
### Right sidebar
### Environment selector and variables pane
### Quick Help

## Footer
