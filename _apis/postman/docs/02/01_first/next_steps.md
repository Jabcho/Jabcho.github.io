---
title: Take your next steps in Postman
project_id: postman   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/postman/02/01_first/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
지금까지 요청을 보내고, 테스트를 작성하고, 요청을 컬렉션에 저장하는 방법을 배웠습니다. 이제 Postman에서 할 수 있는 다른 작업들을 살펴보세요.

- [컬렉션을 직접 실행]({% link _apis/postman/05.md %}#run-collections)하거나, 클라우드에서 특정 시간에 자동으로 실행되도록 설정할 수 있습니다. 또한 [Postman CLI]({% link _apis/postman/05.md %}#postman-cli)나 [Newman]({% link _apis/postman/05.md %}#newman-cli)을 사용해 CI/CD 파이프라인 안에서 컬렉션이 자동으로 실행되도록 할 수 있습니다.

- [Postman Flows]({% link _apis/postman/09.md %}#build-api-first-apps-with-postman-flowsa-visual-low-code-editor)는 API 중심 환경에서 API 기반 애플리케이션을 시각적으로 구성할 수 있는 도구입니다. 요청을 연결하고, 데이터를 처리하고, 실제 서비스 환경과 유사한 워크플로를 Postman 워크스페이스 안에서 구현할 수 있습니다.

- Postman은 [Spec Hub]({% link _apis/postman/07.md %}#design-apis-with-specifications)나 [API Builder]({% link _apis/postman/07.md %}#develop-apis-with-the-api-builder)를 통해 API를 설계하는 API-First 개발 방식을 지원합니다. 이렇게 작성한 API 사양은 프로젝트의 단일 스펙 역할을 할 수 있습니다. 또한 컬렉션을 활용하여 API를 설계할 때는 [컬렉션 타입]({% link _apis/postman/07.md %}#design-apis-with-collections)을 이용할 수 있습니다.

- 컬렉션이나 API를 사용하기 위해서는 문서의 역할이 중요합니다. 컬렉션과 API, 그리고 각 요청의 역할에 대한 사용자 이해를 돕기 위한 [문서를 추가]({% link _apis/postman/06.md %})할 수 있습니다. 기본적으로 문서는 비공개 상태이지만, 공개 API를 만드는 경우 문서를 게시하여 인터넷상의 누구나 접근할 수 있게 할 수 있습니다.

- 2천만 명 이상의 사용자를 보유한 세계 최대의 공개 API 네트워크인 [Postman API Network에 API를 등록]({% link _apis/postman/12.md %})하세요. 등록된 API는 Postman API network에서 앱을 통해 검색할 수 있습니다.
