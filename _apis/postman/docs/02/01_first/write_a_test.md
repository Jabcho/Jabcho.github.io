---
title: Write your first test
project_id: postman   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/postman/02/01_first/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
API 테스트는 API가 기대한 대로 동작하는지 확인하는 방법입니다. 예를 들어, 불완전한 데이터나 잘못된 파라미터를 포함한 요청을 보내서 오류 처리 로직이 정상적으로 작동하는지 검증할 수 있습니다.

Postman에서는 Javascript로 테스트 코드를 작성해서 개별 요청(Request), 컬렉션(Collection), 폴더 단위마다 코드를 추가할 수 있습니다. Postman에서 제공되는  기본 코드 스니펫(snippet)을 이용해 원하는 테스트 로직에 맞게 추가하고 수정할 수 있습니다.

테스트 작성 방법은 다음과 같습니다:

1. [첫 번째 API 요청 보내기]({% link _apis/postman/docs/02/01_first/send_a_request.md %})에서 만든 요청으로 이동합니다.

2. 요청 화면에서 **Scripts** 탭과 **Post-response**를 순서대로 클릭합니다.

코드 에디터 우측 하단의 </> **Snippets 아이콘**과 **Status code: Code is 200** 항목을 순서대로 클릭합니다. 그러면 아래와 같은 테스트 코드가 자동으로 입력됩니다:

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

4. **Send** 버튼을 클릭합니다.

요청이 실행되면 테스트도 함께 실행됩니다. 응답(Response) 섹션에서 **Test Results**를 클릭하여 테스트 결과를 확인합니다.

더 자세한 테스트 작성 방법은 [Postman에서 API 응답 데이터를 검증하는 스크립트 작성하기]({% link _apis/postman/docs/04/01_scripts/write_tests.md %}) 문서를 참고하세요.
