# 웹챗



## 연동화면 예시 <a id="undefined"></a>

CLOSER Builder로 작성된 챗봇은 운영중인 홈페이지에 삽입하거나, 링크 주소를 통해 고객에게 제공될 수 있습니다.

![](../../.gitbook/assets/image%20%289%29.png)

## 연동 방법 <a id="undefined-1"></a>

> 1. CLOSER Builder\(https://builder.closer.ai\)로 이동하여 연동하고자 하는 봇 관리페이지로 진입합니다.
> 2. 좌측 메뉴 Settings &gt; 메신져 연동으로 진입합니다.
> 3. 메신저 연동 &gt; 웹챗 &gt; '설정' 버튼을 클릭합니다.

![&#xBD07; &#xAD00;&#xB9AC; &#xD398;&#xC774;&#xC9C0; &amp;gt; Settings &amp;gt; &#xBA54;&#xC2E0;&#xC800; &#xC5F0;&#xB3D9;](../../.gitbook/assets/image%20%285%29.png)

> 1. 웹챗 활성화 스위치를 ON으로 변경합니다.
> 2. 웹챗이 활성화되면 아래와 같이 script와 주소가 출력됩니다.
>    1. 스크립트를 복사하여 **&lt;body /&gt; 안에 삽입하면 웹챗 버튼이 출력되면서** 바로 웹챗이 연동됩니다.
>    2. 스크립트 아래의 **URL을 활용하시면 IFrame을 통해 별도로 노출하거나, 고객에게 웹챗 주소를 직접 전달할 수 있습니다.**

![&#xBA54;&#xC2E0;&#xC800; &#xC5F0;&#xB3D9; &amp;gt; &#xC6F9;&#xCC57; &#xC124;&#xC815; &amp;gt; &#xC6F9;&#xCC57; &#xD65C;&#xC131;&#xD654; ON](../../.gitbook/assets/image%20%2811%29.png)

## 커스터마이징 <a id="undefined-2"></a>

CLOSER 의 웹챗은 간단하게 커스텀하여 다양한 형태로 사용할 수 있습니다.

![&#xD14C;&#xB9C8;&#xC0C9;&#xC744; &#xBCC0;&#xACBD;&#xD55C; &#xC6F9;&#xCC57; &#xC608;&#xC2DC;](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LIi54aBS9X3UFC1TBaY%2F-LRjk85TIFJ7jGnyiSXy%2F-LRjkOg6tmtXnYS2_KF9%2Fimage.png?alt=media&token=470aa2b7-9782-4411-a3cc-352b855deeab)

웹챗 연동팝업 하단의 `웹챗 커스터마이징` 을 클릭하면, 아래와 같이 커스터마이징 폼이 활성화됩니다.

![&#xBD07; &#xAD00;&#xB9AC; &#xD398;&#xC774;&#xC9C0; &amp;gt; Settings &amp;gt; &#xBA54;&#xC2E0;&#xC800; &#xC5F0;&#xB3D9; &amp;gt; &#xC6F9;&#xCC57; &#xCEE4;&#xC2A4;&#xD130;&#xB9C8;&#xC774;&#xC9D5;](../../.gitbook/assets/image%20%284%29.png)

`웹챗 제목, 웹챗 설명` : 처음 사용자가 웹챗에 들어왔을 때 보여지는 봇에 대한 제목 및 설명을 설정합니다.

`사용자에게 보여질 팝업 메시지 활성화`: 버튼과 함께 출력되는 팝업 메시지를 노출할지 설정합니다.

`팝업메시지` : 버튼과 함께 출력되는 팝업 메시지 내용을 설정합니다.

`테마색` : 웹챗의 전체적인 테마색을 설정합니다. \(배경, 말풍선, 전송 버튼 등\)

`버튼 아이콘 변경` : 버튼안에 삽입되는 아이콘 이미지를 변경할 수 있습니다.

`버튼 위치` : 삽입될 버튼이 홈페이지의 좌측, 우측 하단에 보여질지 설정합니다.

`버튼 아이콘 사이즈` : 버튼안에 삽입되는 아이콘 이미지의 크기를 변경할 수 있습니다. 최대 60px까지 지원하며 최대 사이즈로 설정하실 경우 배경색 없이 이미지만 출력되어 이미지를 통해 원하는 대로 커스텀 하실 수 있습니다.

`버튼 border-radius` : 버튼의 border-radius 값을 설정합니다.

![&#xC6F9;&#xCC57; &#xCEE4;&#xC2A4;&#xD130; &#xB9C8;&#xC774;&#xC9D5; &amp;gt; &#xBC84;&#xD2BC;/&#xD31D;&#xC5C5;](../../.gitbook/assets/image%20%283%29.png)

커스터마이징을 통해 원하는 웹챗 디자인을 작성하셨다면, **\`저장\` 버튼을 통해 설정을 저장할 수 있습니다.**

**저장된 설정은 자동으로 웹챗에 적용됩니다.**

\*\*\*\*

### CSS Selector를 활용한 버튼 커스터마이징 <a id="css-selector"></a>

위에 설명한 커스텀 이외의 수정이 필요하신 경우 \(버튼 위치 조절, 애니메이션..\) CSS Selector를 활용해 직접 수정하실 수 있습니다.

| selector | 역할 |
| :--- | :--- |
| .closer\_webchat\_chat\_wrapper | 오픈 애니메이션을 커스텀하거나, 위치를 조절 할 수 있습니다. |
| .closer\_webchat\_button\_wrapper |  |

