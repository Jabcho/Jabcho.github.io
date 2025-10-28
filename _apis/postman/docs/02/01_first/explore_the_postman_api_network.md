---
title: Discover public APIs on the Postman API Network
project_id: postman   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/postman/02/01_first/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
Postman API Network는 세계에서 가장 큰 공개 API 네트워크입니다. 개발자는 이 API 네트워크를 통해 다양한 API를 탐색하고, 기여하고, 직접 만들어 배포할 수 있습니다. 여러분이 잘 알고 있는 많은 기업들이 자사의 API를 Postman API Network의 공개 워크스페이스에 게시하고 있습니다.

API를 사용하는 개발자라면, 새롭고 유명한 워크스페이스, 컬렉션, 요청, API, 플로우(Flow), 그리고 팀을 이용할 수 있습니다. 반대로 API를 개발자라면, 게시자 도구(Publisher tools)를 편리하게 이용할 수 있습니다.

Postman API Network를 더 알아보려면, Postman 상단 헤더에서 [API Network](https://www.postman.com/explore/)를 클릭하세요.

![explore_the_postman_api_network]({{ '/assets/img/02/01_first/explore_the_postman_api_network.png' | relative_url }})

## Find public APIs
Postman API Network에서는 공개 워크스페이스, 컬렉션, 요청(Request), API, 플로우(Flow), 그리고 팀을 검색해서 찾아볼 수 있습니다.

### Search public elements
기본적으로 Postman은 사용자가 접근할 수 있는 모든 워크스페이스, 컬렉션, 요청, API, 플로우, 팀을 검색해서 결과를 보여줍니다.

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.open-in-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.open-in-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-open-in.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.search-postman-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.search-postman::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-search-postmanjpg' | relative_url }}") no-repeat center / contain;
}
</style>

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.all-of-postman-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.all-of-postman::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-all-of-postman.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.workspaces-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.workspaces-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-workspaces.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.collections-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.collections-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-collections.jpg' | relative_url }}") no-repeat center / contain;
}
</style>
<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.requests-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.requests-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-requests.jpg' | relative_url }}") no-repeat center / contain;
}
</style>
<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.apis-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.apis-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-apis.jpg' | relative_url }}") no-repeat center / contain;
}
</style>
<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.flows-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.flows-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-flows.jpg' | relative_url }}") no-repeat center / contain;
}
</style>
<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.teams-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.teams-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-teams.jpg' | relative_url }}") no-repeat center / contain;
}
</style>



Postman API Network에서만 검색하려면, Postman 상단 헤더에서 <span class="search-postman-icon"></span> Search Postman을 클릭하세요. 그 다음 <span class="all-of-postman-icon"></span> All of Postman 아이콘을 클릭하고, Search in 항목에서 Public API Network를 선택합니다.

또한 검색 범위를 각각 워크스페이스, 컬렉션, 요청, API, 플로우, 팀 항목 내로 지정할 수 있습니다. 항목별로 검색하려면 **Search for** 오른쪽에서 다음 중 하나를 선택하세요:

- <span class="workspaces-icon"></span> Workspaces

- <span class="collections-icon"></span> Collections

- <span class="requests-icon"></span> Requests

- <span class="apis-icon"></span> APIs

- <span class="flows-icon"></span> Flows

- <span class="teams-icon"></span> Teams

![search_public_elements]({{ '/assets/img/02/01_first/search_public_elements.png' | relative_url }})

### Browse public elements
Postman API Network를 탐색하려면 다음 페이지들을 방문하세요:

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.explore-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.explore-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-explore.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.spotlight-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.spotlight-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-spotlight.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.trending-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.trending-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-trending.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.publishers-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.publishersicon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-publishers.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

<style>
/* 문단(또는 블록인용) 맨 앞에 아이콘을 고정 배치 */
.categories-icon{
  position: relative;
  padding-left: 1rem;            /* 아이콘 공간 확보 */
  margin: 0 0 0 0;
  line-height: 1.65;
}

/* 아이콘 자체 */
.categories-icon::before{
  content: "";
  position: absolute;
  left: 0; top: .2rem;             /* 필요 시 .1~.3rem로 미세 조정 */
  width: 16px; height: 16px;
  background: url("{{ '/assets/img/icons/icon-categories.jpg' | relative_url }}") no-repeat center / contain;
}
</style>

- <span class="explore-icon"></span>Explore — [Explore](https://www.postman.com/explore/) 페이지는 Postman API Network의 메인 페이지로, Postman이 직접 선정한 주목할 만한 공개 워크스페이스, 컬렉션, API, 플로우와 함께 커뮤니티에서 인기 있는 항목들이 소개됩니다.

- <span class="spotlight-icon"></span>Spotlight — [Spotlight](https://www.postman.com/explore/spotlight/) 페이지는 Postman이 커뮤니티에서 직접 선정한 워크스페이스, 컬렉션, API, 플로우의 모범 사례들을 모아둔 페이지입니다.

- <span class="trending-icon"></span>Trending — [Trending](https://www.postman.com/explore/trending-apis/) 페이지는 워크스페이스, 컬렉션, API, 플로우를 조회수, 활동 및 사용 빈도가 높은 순서대로 보여줍니다.

- <span class="publishers-icon"></span>Publishers — [Publishers](https://www.postman.com/explore/publishers?sort=featured&page=1) 페이지는 공개 워크스페이스, 컬렉션, 또는 플로우를 게시한 팀 목록을 보여줍니다. 오른쪽 상단에서 Featured, New, Most Viewed로 정렬 및 필터링할 수 있습니다.

- <span class="workspaces-icon"></span> Workspaces — [Workspaces](https://www.postman.com/explore/workspaces/) 페이지는 공개 워크스페이스 목록을 보여줍니다. 오른쪽 상단에서 Featured, New, Week, All Time으로 정렬 및 필터링할 수 있습니다.

- <span class="collections-icon"></span> Collections — [Collections](https://www.postman.com/explore/collections/) 페이지는 공개 컬렉션 목록을 보여줍니다. 오른쪽 상단에서 Featured, New, Week, All Time으로 정렬 및 필터링할 수 있습니다.

- <span class="flows-icon"></span> Flows — [Flows](https://www.postman.com/explore/flows/) 페이지는 공개 플로우 목록을 보여줍니다. 오른쪽 상단에서 New, Most Viewed, Most Forked로 정렬 및 필터링할 수 있습니다.

- <span class="categories-icon"></span> Categories — [Categories](https://www.postman.com/categories/) 페이지는 Postman이 선정한 카테고리 목록을 보여줍니다. 각 카테고리별로 공개 워크스페이스, 컬렉션, 플로우를 확인할 수 있습니다. 오른쪽 상단에서 New, Most Viewed, Most Forked로 정렬 및 필터링할 수 있습니다.

### Get started with public elements
Postman API Network에서 공개 API를 바로 사용해보고 싶다면, 다음 컬렉션들을 확인해보세요:

- [Learn by API](https://www.postman.com/apilearningresources/api-learning-resources/collection/vcbuqdx/learn-by-api)

- [API Learner](postman.com/apilearningresources/api-learning-resources/collection/6izoy0h/api-learner?ctx=documentation)

- [Public REST APIs](https://www.postman.com/cs-demo/public-rest-apis/overview)

- [Intro to writing tests](https://www.postman.com/postman/postman-team-collections/collection/9fqcfpk/intro-to-writing-tests-with-examples)

- [How to use the Postman Console](https://www.postman.com/postman/postman-team-collections/collection/c8w949c/how-to-use-the-postman-console?ctx=documentation)

- [Postman Echo](https://www.postman.com/postman/published-postman-templates/documentation/ae2ja6x/postman-echo)

## Next steps
- Postman 공식 인증 팀의 공개 API를 선택하고 싶다면 [공개 항목 선택하기]({% link _apis/postman/docs/12/01_explore/consume_public_apis.md %}#choose-public-elements)를 참고하세요.

- 공개 항목을 포크(fork)하여 복제하고 싶다면 [공개 항목 사용하기]({% link _apis/postman/docs/12/01_explore/consume_public_apis.md %}#use-public-elements)를 참고하세요.

- 공개 항목을 구독(Watch)하고 싶다면 [공개 항목 팔로우하기]({% link _apis/postman/docs/12/01_explore/consume_public_apis.md %}#watch-public-elements)를 참고하세요.
