---
title: Send your first API request
project_id: postman   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/postman/02/01_first/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
Postman의 API 클라이언트는 HTTP, GraphQL, gRPC 요청을 포함한 다양한 API 요청을 생성하고 전송할 수 있도록 지원합니다. Postman을 사용하면 API 엔드포인트로 요청을 보내거나, 데이터 소스에서 데이터를 조회하거나, API의 기능을 테스트할 수 있습니다. 터미널에 명령어를 입력하거나 코드를 작성할 필요는 없습니다. 새로운 요청을 만든 뒤 **Send** 버튼을 클릭하면, Postman 안에서 바로 API 응답을 받을 수 있습니다.

## Send an API request
[Postman 데스크톱 앱을 다운로드하고 설치]({% link _apis/postman/docs/02/01_first/download.md %})했는지 확인하세요. 준비가 되면 Postman 데스크톱 앱을 열고 첫 번째 API 요청을 보내보세요.

1. 워크벤치에서 **Add 아이콘**(➕)을 클릭해 새 [탭]({% link _apis/postman/docs/02/02_basics/the_postman_interface.md %}#opening-a-new-tab)을 엽니다.

2. 요청 URL로 "postman-echo.com/get"을 입력합니다.

3. **Send** 버튼을 클릭합니다.

Postman 하단 창에는 서버에서 전송된 응답 데이터가 표시됩니다.

![send_an_api_request]({{ '/assets/img/02/01_first/send_an_api_request.png' | relative_url }})

## How it works
이 예제에서 Postman은 클라이언트로 동작하며 API 서버와 통신합니다. **Send**를 클릭하면 다음과 같은 과정이 진행됩니다:

1. Postman이 GET 요청을 postman-echo.com의 [Postman Echo API](https://www.postman.com/postman/published-postman-templates/documentation/ae2ja6x/postman-echo?ctx=documentation) 서버로 전송합니다.

2. API 서버가 요청을 수신하고 처리한 뒤, Postman으로 응답을 돌려보냅니다.

3. Postman이 응답을 수신하고 Response 패널에 표시합니다.

이와 같이 Postman으로 간단하게 API 요청을 보내고 API 서버로부터 응답을 받을 수 있습니다.

![how_it_works]({{ '/assets/img/02/01_first/how_it_works.png' | relative_url }})

## Next steps
첫 API 요청을 보냈으니, 이제 Postman의 더욱 다양한 기능을 배워보세요!

- Postman Echo API로 다양한 요청을 보내보세요. Postman에서 요청을 손쉽게 시험해 볼 수 있습니다. Echo API에 대한 자세한 내용은 [Postman Echo API 문서]({% link _apis/postman/docs/13/02_echo/postman_echo_service.md %}#create-requests)를 참고하세요.

- Postman에서 요청을 구성하고 보내는 방법은 [Postman에서 API 요청 만들고 보내기]({% link _apis/postman/03.md %}) 가이드에서 이어서 학습할 수 있습니다.

<div style="
  border:1px solid rgba(33,150,243,.35);
  background:rgba(33,150,243,.08);
  border-radius:14px;
  padding:18px 22px;
  display:flex; align-items:center; justify-content:space-between; gap:16px;
  box-shadow:0 2px 0 rgba(33,150,243,.08);
">
  <!-- 왼쪽: 아이콘 + 텍스트 -->
  <div style="display:flex; align-items:center; gap:12px;">
    <!-- 배경 없는 SVG 아이콘 -->
    <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" aria-hidden="true" style="flex:0 0 auto">
      <path fill="#606770" d="M16 11a4 4 0 1 0-3.999-4A4 4 0 0 0 16 11m-8 0a4 4 0 1 0-3.999-4A4 4 0 0 0 8 11"/>
      <path fill="#606770" d="M2 20.5A5.5 5.5 0 0 1 7.5 15h1A5.5 5.5 0 0 1 14 20.5V21H2zM10 21v-.5A5.5 5.5 0 0 1 15.5 15h1A5.5 5.5 0 0 1 22 20.5V21z" opacity=".8"/>
    </svg>

    <div style="line-height:1.35;">
      <div style="font-weight:700; font-size:1.05rem;">
        디버깅에 대한 도움이 필요한가요? 다른 개발자들에게 물어보세요.
      </div>
    </div>
  </div>
