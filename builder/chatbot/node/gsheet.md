# 구글 스프레드 시트 노드 👩🏻‍🔬

**구글 스프레드시트 노드**는 사용자가 입력한 정보를 구글 스프레드 시트에 기록하고 저장하기 위해 사용하는 노드 입니다.

### 설정 방법

* 먼저 [프로필 설정 &gt; 연결된 계정 관리 ](../../../platform/settings/integration.md)메뉴에서 구글 계정을 연동을 진행해 주신 후, 노드 설정 화면의 token값에 해당 프로필을 선택해줍니다.

![&#xAD6C;&#xAE00; &#xACC4;&#xC815; &#xC5F0;&#xACB0; &#xC608;&#xC2DC;](../../../.gitbook/assets/integrations.png)

* 구글 스프레드 시트 주소 표시줄에서 spreadsheetId를 찾아 입력합니다.  아래 표시된 부분입니다.

![](../../../.gitbook/assets/guide_google-spreadsheet-id.png)

* 시트명\(sheetName\), 컬럼명\(columns\), 값\(values\)을 입력해두면 사용자가 입력한 값이 지정한 시트에 입력됩니다. 이 때, 일치하는 시트명이 없으면 새로운 시트가 생성됩니다.

* 아래는 사용자가 입력한 메시지를 파라미터로 저장하여 시트에 입력받는 예시 입니다.  사용자가 입력한 이름\(name\) 값은 이름 열에, 전화번호\(phonenumber\) 값은 전화번호 열에 기록됩니다.

![&#xAD6C;&#xAE00; &#xC2A4;&#xD504;&#xB808;&#xB4DC;&#xC2DC;&#xD2B8; &#xB178;&#xB4DC; &#xC0AC;&#xC6A9; &#xC608;&#xC2DC;](../../../.gitbook/assets/guide_google-spreadsheet.png)



### \*\*\*\* <a id="agent-call-node"></a>

