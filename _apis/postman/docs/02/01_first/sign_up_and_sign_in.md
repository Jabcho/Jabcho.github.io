---
title: Sign up for Postman
project_id: postman   # ← 01.md, contents.md와 동일하게
is_contents: false   # Contents 문서가 아니라면 기본 false (생략 가능)
active_url: /api/postman/02/01_first/
nav_order: 2  
---

> 이 문서는 공식 레퍼런스를 바탕으로 한 한국어 번역·주해본입니다.  
> 전체 목차는 [Contents]({{ '/api/' | append: page.project_id | append: '/contents/' | relative_url }})에서 확인하세요.

<br>
Postman 계정을 등록하기 전에 Postman 데스크톱 앱을 다운로드하거나 Postman에 웹에 접속하세요. 자세한 내용은 [Postman 앱 다운로드]({% link _apis/postman/docs/02/01_first/download.md %}) 문서를 참고하세요.

[Postman 데스크톱 앱]({% link _apis/postman/docs/02/01_first/download.md %})에 로그인을 하지 않았다면 [경량 Postman API Client]({% link _apis/postman/docs/02/02_basics/lightweight_api_client.md %}) 환경에서 작업할 수 있습니다. 이 환경에서는 요청(Request)을 작성하고 전송할 수 있습니다. 작업 내용을 동기화 요청들을 컬렉션(Collection)으로 정리하기, 협업하기 등의 기타 다른 기능들을 이용하려면 무료 계정을 만들고 [로그인](#sign-in-to-postman)하세요.

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
        Postman 계정 관리에 대한 자세한 내용은 [Postman 계정]({% link _apis/postman/02.md %}#your-postman-account) 문서를 참고하세요.
    </div>
  </div>
</div>

## Sign up for Postman
Postman 계정을 만드는 방법은 다음과 같습니다:

1. 데스크톱 앱 우측 상단의 **Create Account** 버튼을 클릭하거나 Postman 웹사이트에서 **Sign up for free** 버튼을 클릭합니다.

2. 다음 중 원하는 방식을 선택할 수 있습니다:

     - 이메일로 가입 : 이메일 주소를 입력하고 사용자 이름과 비밀번호를 설정한 뒤, **Create Free Account**를 클릭합니다.

      Postman을 사용하기 전에 계정 인증 절차가 필요합니다. 이메일로 전송된 6자리 인증 코드를 입력하고 **Verify Account**를 클릭하세요.

인증 메일을 받지 못한 경우 Resend verification code를 클릭해 다시 받을 수 있습니다.

인증 과정에서 문제가 발생하면 **지원 요청(Help request)**을 제출하세요.

▪ GitHub 계정으로 가입

Sign up with GitHub을 클릭하면 GitHub 인증 페이지로 이동합니다.
GitHub 계정에 연결된 이메일을 선택해 가입을 진행하세요.

▪ Google 계정으로 가입

Sign up with Google을 클릭하고 안내에 따라 로그인합니다.

▪ SSO(Single Sign-On)로 가입

조직에서 SSO(싱글 사인온)를 설정한 팀이 있다면,
Sign in with SSO를 클릭해 로그인할 수 있습니다.

1. 로그인 유지 설정

30일 동안 로그인 상태를 유지하려면 Stay signed in을 선택하세요.
자세한 내용은 Postman 로그인하기
 문서를 참고하세요.

4. 기본 정보 입력

Create Free Account를 클릭한 후, 이름과 역할(Role)을 입력하고
Postman을 어떤 용도로 사용할지 선택합니다.
이 정보는 맞춤형 환경 구성을 위해 사용됩니다.
입력이 끝나면 Continue를 클릭하세요.

5. 팀 참여 또는 건너뛰기

첫 번째 팀에 참여하거나 Skip을 클릭해 건너뛸 수 있습니다.

회사 이메일로 가입하고, 회사 계정에 Team Discovery 기능이 활성화되어 있다면
가입 가능한 팀 목록이 표시됩니다.

초대 링크를 통해 가입한 경우, 해당 팀의 **워크스페이스(Workspace)**에 자동으로 접근할 수 있습니다.
자세한 내용은 워크스페이스 알아보기
를 참고하세요.

Free 또는 Basic 요금제로 가입하면, 개인 팀이 자동으로 생성됩니다.
이후 동료를 초대해 함께 사용할 수도 있습니다.
자세한 내용은 팀 생성 및 협업
 문서를 참고하세요.

6. 요금제 선택

이용할 요금제를 선택하거나 Continue with Free Plan을 클릭해 무료 요금제로 진행하세요.

7. 팀 설정

팀 이름을 수정하고, 공유 링크 또는 이메일로 다른 사용자를 초대할 수 있습니다.
설정이 끝나면 Continue를 클릭하세요.

💡 도메인 사용자 주의사항

회사 이메일(@company.com)을 사용하는 경우,
기본 설정으로 팀이 자동 검색(Team Discovery) 가능 상태입니다.

동일한 도메인을 사용하는 사용자는 링크를 통해 자동으로 팀에 참여할 수 있습니다.

언제든지 팀 설정 페이지에서 이 옵션을 변경할 수 있습니다.

8. Postman 사용 목적 응답

Postman 사용 목적을 묻는 화면에서 Let’s Go를 클릭하거나 Skip을 선택하세요.
선택한 용도에 따라 맞춤형 테스트 워크스페이스가 자동 생성됩니다.

9. 프로필 및 동기화 설정

새로 생성된 Postman 프로필은 협업자 및 공유 리소스 접근자에게 표시됩니다.
프로필 수정 방법은 Postman 프로필 설정
 문서를 참고하세요.

또한, 작업 내용을 **동기화(Sync)**하여 여러 기기에서 접근할 수 있으며,
계정 설정 관련 자세한 내용은 Postman 계정 설정 알아보기
에서 확인할 수 있습니다.

## Sign in to Postman
Postman 데스크톱 앱 우측 상단의 Sign In 버튼을 클릭해 로그인할 수 있습니다.
또는 Postman 웹사이트 우측 상단의 Sign In을 눌러 로그인하면, 브라우저에서 여러 API 개발 및 테스트 작업을 수행할 수 있습니다.

데스크톱 앱에서 Sign In을 클릭하면, 브라우저로 이동해 로그인을 진행할 수 있도록 새 화면이 열립니다. 기본 브라우저가 자동으로 실행되어 로그인 페이지가 열립니다. 만약 브라우저가 몇 초 안에 열리지 않는다면 수동으로 **열기(open it manually)**를 클릭하거나 표시된 **URL을 복사**해 직접 접속할 수 있습니다.

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
        로그인을 건너뛰고 바로 앱으로 이동하려면 **Skip and take me to Postman Desktop App**을 클릭하세요.
    </div>
  </div>
</div>

Postman 계정 정보를 입력하거나, 구글 계정으로 로그인할 수 있습니다. SSO(Single Sign-On)가 설정된 Postman Enterprise 팀 계정으로 로그인할 경우, **Sign in with SSO**를 선택하세요. 자세한 내용은 [Sign in to an SSO team]({% link _apis/postman/01.md %}#administer-postman) 문서를 참고하세요.

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
        처음으로 SSO로 로그인하는 경우, [계정을 Postman에 연결]({% link _apis/postman/docs/02/03_account/manage_your_account.md %})해야 할 수 있습니다.
    </div>
  </div>
</div>

**Stay signed in**을 선택하면 최대 30일 동안 로그인 상태가 유지됩니다. 30일 동안 활동이 없으면 재인증이 필요합니다. 작업하는 기기에서 로그인 상태를 유지하고 싶지 않다면 이 옵션을 해제하세요. 활동이 없는 상태로 30분이 지나면 Postman 재로그인이 필요합니다.

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
        팀에서 모든 멤버들의 로그인 최대 유지 시간을 설정해둔 경우, 그 설정에 따라 세션이 자동으로 종료됩니다.
    </div>
  </div>
</div>

[2단계 인증]({% link _apis/postman/docs/02/03_account/manage_postman_settings.md %}#set-up-two-factor-authentication) (2FA)을 설정한 계정이라면, 인증 앱(Authenticator App)에 표시된 인증 코드를 입력하고 **Verify**를 클릭하세요.

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
        기기 분실 등으로 인증 앱에 접근할 수 없는 경우 **Use a recovery code**를 클릭하세요. 복구 코드도 분실한 경우 등록된 이메일 주소를 통해 [Postman 지원팀에 문의](help@postman.com)하세요.
    </div>
  </div>
</div>

로그인이 완료되면 자동으로 Postman 데스크톱 앱으로 돌아갑니다.

여러 개의 Postman 팀에 속해 있고 각 팀이 서로 다른 인증 방식을 사용하는 경우, 각 팀에 별도로 로그인해야 합니다. 이 경우 헤더의 아바타를 클릭하여 접속할 팀을 선택하세요.

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
        Postman 데스크톱 앱에서 로그인 절차는 시작 후 5분 이내에 완료해야 합니다. 제한 시간을 초과한 경우, 데스크톱 앱으로 돌아가 로그인 과정을 다시 시작해야 합니다.
    </div>
  </div>
</div>


