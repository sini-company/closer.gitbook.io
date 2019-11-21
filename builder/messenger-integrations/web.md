---
description: '홈페이지에 챗봇과 대화하는 버튼을 삽입하거나, 챗봇과 대화 가능한 링크를 생성하는 방법을 확인하세요.'
---

# 웹사이트 연동

![CLOSER &#xCC44;&#xD305; &#xC5F0;&#xB3D9; &#xC608;&#xC2DC;](../../.gitbook/assets/image%20%2832%29.png)

CLOSER에서는 웹사이트에 실시간 채팅을 연동할 수 있도록 다음 두 가지 연동 방식을 제공합니다.

1. 웹 페이지에 실시간 채팅 javascript 삽입 방식 
   * 가장 쉽게 연동 가능한 방식으로, 연동하고자 하는 웹페이지의 하단에 CLOSER 웹 채팅 팝업 버튼을 노출하는 스크립트를 삽입하는 방입니다. 
2. 웹 채팅 페이지 URL 직접 접근 방식
   * 팝업 형태로 제공되는 웹 채팅 페이지를 직접 사용자들에게 제공하는 방식입니다. 문자 메세지 등을 통한 아웃바운드 마케팅 링크나 직접 iframe을 통해 웹 채팅의 노출 시점을 관리하고자 할 때 사용합니다..

## 설정 방법 <a id="undefined-1"></a>

1. 연동하고자 하는 챗봇의 **메신저 연동** 메뉴로 진입합니다.
2. 메신저 연동 페이지에서 **웹챗** 항목의 **설정** 버튼을 클릭합니다.

![&#xBD07; &#xAD00;&#xB9AC; &#xD398;&#xC774;&#xC9C0; &amp;gt; Settings &amp;gt; &#xBA54;&#xC2E0;&#xC800; &#xC5F0;&#xB3D9;](../../.gitbook/assets/image%20%2821%29.png)

![&#xBA54;&#xC2E0;&#xC800; &#xC5F0;&#xB3D9; &amp;gt; &#xC6F9;&#xCC57; &#xC124;&#xC815; &amp;gt; &#xC6F9;&#xCC57; &#xD65C;&#xC131;&#xD654; ON](../../.gitbook/assets/image%20%2835%29.png)

**웹챗 활성화** 스위치를 활성화하시면 웹 채팅은 즉시 활성화되고, 언제든 같은 방법으로 비활성화가 가능합니다. 

## 테마 설정 <a id="undefined-2"></a>

CLOSER가 제공하는 웹 채팅 위젯은 현재 색상이나 버튼 등의 간단한 커스터마이징을 지원하고 있으며, 점점 더 다양한 커스터마이징을 지원할 예정입합니다.

![&#xD14C;&#xB9C8;&#xC0C9;&#xC744; &#xBCC0;&#xACBD;&#xD55C; &#xC6F9; &#xCC44;&#xD305; &#xC704;&#xC82F; &#xC608;&#xC2DC;](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LIi54aBS9X3UFC1TBaY%2F-LRjk85TIFJ7jGnyiSXy%2F-LRjkOg6tmtXnYS2_KF9%2Fimage.png?alt=media&token=470aa2b7-9782-4411-a3cc-352b855deeab)

웹사이트 연동 설정 하단의 **`웹챗 커스터마이징`** 메뉴를 열어보시면 아래와 같이 커스터마이징 설정 화면을 확인할 수 있습니다.

![&#xBD07; &#xAD00;&#xB9AC; &#xD398;&#xC774;&#xC9C0; &amp;gt; Settings &amp;gt; &#xBA54;&#xC2E0;&#xC800; &#xC5F0;&#xB3D9; &amp;gt; &#xC6F9;&#xCC57; &#xCEE4;&#xC2A4;&#xD130;&#xB9C8;&#xC774;&#xC9D5;](../../.gitbook/assets/image%20%2820%29.png)

* `웹챗 제목, 웹챗 설명` : 처음 사용자가 웹챗에 들어왔을 때 보여지는 봇에 대한 제목 및 설명을 설정합니다.
* `사용자에게 보여질 팝업 메시지 활성화`: 버튼과 함께 출력되는 팝업 메시지를 노출할지 설정합니다.
* `팝업메시지` : 버튼과 함께 출력되는 팝업 메시지 내용을 설정합니다.\(HTML 사용가능\)
* `테마색` : 웹챗의 주 테마 색상을 설정합니다. \(배경, 말풍선, 전송 버튼 등\)
* `버튼 아이콘 변경` : 버튼안에 삽입되는 아이콘 이미지를 변경할 수 있습니다.
* `버튼 위치` : 삽입될 버튼이 홈페이지의 좌측, 우측 하단에 보여질지 설정합니다.
* `버튼 아이콘 사이즈` : 버튼안에 삽입되는 아이콘 이미지의 크기를 변경할 수 있습니다. \(최대 60px까지 지원\)
* `버튼 border-radius` : 버튼의 가장자리의 둥근 정도를 설정합니다.

![&#xC6F9;&#xCC57; &#xCEE4;&#xC2A4;&#xD130; &#xB9C8;&#xC774;&#xC9D5; &amp;gt; &#xBC84;&#xD2BC;/&#xD31D;&#xC5C5;](../../.gitbook/assets/image%20%2836%29.png)

### CSS Selector를 활용한 버튼 커스터마이징 👩🏻‍🔬 <a id="css-selector"></a>

위에서 제공된 설정 이외에 웹 채팅 버튼이나 웹 채팅을 담게 될 컨테이너의 위치나 크기 등의 수정이 필요하신 경우, CSS Selector를 이용해 조금 더 다양한 속성을 설정할 수 있습니다.

| selector | 역할 |
| :--- | :--- |
| .closer\_webchat\_chat\_wrapper | 오픈 애니메이션을 커스텀하거나, 위치를 조절 할 수 있습니다. |
| .closer\_webchat\_button\_wrapper | Button의 위치를 조절하거나, 최초 등장 애니메이션을 커스텀할 수 있습니다. |

![css selector&#xB97C; &#xC774;&#xC6A9;&#xD574; &#xBC84;&#xD2BC; &#xD06C;&#xAE30;&#xB97C; &#xC870;&#xC808;&#xD55C; &#xC608;&#xC2DC;](../../.gitbook/assets/2019-04-04-10.42.29.png)

* 현재 설정 가능한 css selector는 채팅창 버튼과 채팅창을 보여주게 될 container element에 한정됩니다.
* 내부 말풍선 모양이나 폰트 크기 조절은 추후 지원될 예정입니다.

