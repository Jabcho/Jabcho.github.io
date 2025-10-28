---
title: Create your first collection
project_id: postman   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/postman/02/01_first/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
새로운 [컬렉션]({% link _apis/postman/docs/02/02_basics/postman_elements.md %}#collections)을 만들기 위해, 이번 예시에서는 먼저 새 요청(request)을 생성하는 것부터 시작합니다. Postman의 사이드바에서 새 요청을 만들 수 있습니다.

새 컬렉션을 만들고 그 안에 요청을 저장하려면 다음 단계를 따르세요:

1. 아직 Postman 데스크톱 앱을 설치하지 않았다면, [Postman 데스크톱 앱을 설치]({% link _apis/postman/docs/02/01_first/download.md %})한 뒤 [로그인]({% link _apis/postman/docs/02/01_first/sign_up_and_sign_in.md %})하세요.

2. New > HTTP를 클릭합니다.

![create_your_first_collections]({{ '/assets/img/02/01_first/create_your_first_collections.png' | relative_url }})

3. 요청 빌더(request builder)에 요청을 입력하고 **Save**를 클릭합니다.

4. **New Collection**을 클릭하고, 요청과 컬렉션 이름을 각각 지정합니다.

![create_your_first_collections_2]({{ '/assets/img/02/01_first/create_your_first_collections_2.png' | relative_url }})

5. **Save**를 클릭하면 해당 요청이 컬렉션에 추가됩니다.

요청을 저장하면 새 컬렉션과 요청이 사이드바의 **Collections** 섹션에 표시됩니다.

![create_your_first_collections_3]({{ '/assets/img/02/01_first/create_your_first_collections_3.png' | relative_url }})

Postman에서 보낸 모든 요청은 사이드바의 **History** 탭에 표시됩니다. 소규모 작업에서는 이 기록을 통해 이전 요청을 재사용하는 것이 편리하지만, Postman 사용량이 많아질수록 기록에서 특정 요청을 찾는 데 시간이 오래 걸릴 수 있습니다. 따라서 매번 기록을 찾는 대신, 모든 요청을 컬렉션에 저장해두면 훨씬 빠르고 효율적으로 접근할 수 있습니다.

### Next steps
- 컬렉션에 대해 더 알아보려면 [Collections 개요]({% link _apis/postman/05.md %}) 문서를 확인하세요.

- 컬렉션 생성, 편집, 삭제, 작업 방법은 [Postman에서 요청 컬렉션 생성 및 관리하기]({% link _apis/postman/05.md %}#create-and-manage-collections) 문서를 참고하세요.

- 컬렉션 실행 방법에 대한 자세한 내용은 [Collection Runner 개요]({% link _apis/postman/05.md %}#run-collections)를 확인하세요.
