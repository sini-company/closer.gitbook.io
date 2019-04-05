---
description: 챗봇이 고객에게 전송할 메시지를 설정하는 노드
---

# 메시지 응답 노드

![&#xBA54;&#xC2DC;&#xC9C0; &#xC751;&#xB2F5; &#xB178;&#xB4DC;](../../../.gitbook/assets/flow_editor_response_node.png)

메시지 응답 노드는 **챗봇이 고객에게 전송하는 메시지**를 설정하는 노드 입니다.

CLOSER에서는 다음 네 가지 형태의 메시지를 지원공하고 있습니다.

* 텍스트 메시지
* 미디어 메시지 \(이미지, 동영상, 오디오\)
* 카드형 메시지 \(캐러셀\)
* 위치 메시지 👩🏻‍🔬

각 유형별 메시지 설정 방법은 아래 기본 설정 항목을 참고해 주세요.

{% hint style="warning" %}
각 메시징 채널마다 설정된 길이 제한이나 기능 지원 여부가 모두 다릅니다.  
때문에 CLOSER에서 설정한 메시지가 연동한 메신저에 제대로 표시되지 않을 가능성이 있습니다. 그러한 경우 아래 사항들을 확인해주세요. 

* **길이 제한을 초과한 경우**: 초과한 텍스트는 말줄임표\(`...`\)로 대체됩니다. 
* **지원하지 않는 위젯의 경우**: 해당 위젯이 표시되지 않습니다. \(예: 말풍선 버튼\)
* **카드의 갯수나 버튼 갯수를 초과한 경우**: 초과한 항목들은 생략되거나, 가능한 경우 메시지를 나누어서 전송합니다.
* **지원하지 않는 미디어 유형의 경우**: 지원하지 않는 미디어라고 표시되거나 웹 링크로 대체됩니다.

각 메시징 채널 별 지원 여부에 대해서는 [메신저 연동 &gt; 지원 여부 테이블](../../messenger-integrations/#availability-table) 문서를 확인해주세요.
{% endhint %}

## 전송 가능한 메시지 유형

### 텍스트 메시지 \(text\)

![&#xD14D;&#xC2A4;&#xD2B8; &#xBA54;&#xC2DC;&#xC9C0; &#xC124;&#xC815; &#xD654;&#xBA74;](../../../.gitbook/assets/message-form-text.png)

텍스트 응답 방식은 모든 메시징 채널에서 지원하는 가장 기본적인 **텍스트 말풍선** 응답 방식입니다.

* 일반적인 정적 텍스트에서 나아가 [템플릿을 이용한 메시지 생성](response.md#undefined-4)이 지원됩니다.
* 말풍선에 첨부될 [메시지 버튼](response.md#undefined-2)을 설정할 수 있습니다.

### 미디어 메시지 \(media\)

![&#xBBF8;&#xB514;&#xC5B4; &#xBA54;&#xC2DC;&#xC9C0; &#xC124;&#xC815; &#xD654;&#xBA74;](../../../.gitbook/assets/message-form-media.png)

미디어 메시지에는 사진이나 동영상 또는 음성 형태의 미디어를 설정할 수 있습니다.   
빈 미디어를 클릭하면 ① **URL을 직접 입력**하거나 ② **데스크톱에서 파일을 선택**할 수 있는 팝업 메뉴가 나타나며, 나아가 ③ **파일을 끌어다 놓아서 이미지를 첨부**하거나 ④ **복사 + 붙여넣기를 통해 이미지를 첨부**하는 방법도 지원합니다. 

![&#xBBF8;&#xB514;&#xC5B4; &#xC124;&#xC815; &#xD31D;&#xC5C5; &#xBA54;&#xB274;](../../../.gitbook/assets/message-form-media-popup.png)

![&#xB4DC;&#xB798;&#xADF8; &#xC564; &#xB4DC;&#xB86D;&#xC744; &#xD1B5;&#xD55C; &#xC774;&#xBBF8;&#xC9C0; &#xC5C5;&#xB85C;&#xB4DC;](../../../.gitbook/assets/message-form-media-upload.gif)

CLOSER에서는 이미지 파일에 한하여 파일 첨부 기능을 제공하고 있습니다.   
단, 지나치게 높은 용량의 파일은 업로드 시 화질 손상이 발생할 수 있는 점 유의해주세요.

* 업로드 용량 제한: 10mb 
* 업로드 형식 제한: jpg, gif, png, bmp
* 이미지 크기 제한: 1024 \* 1024 px

{% hint style="warning" %}
메시징 채널 별로 지원하는 미디어의 형식, 크기 등의 제한이 각각 다르게 설정되어 있습니다.  
특정 미디어의 응답을 지원하지 않는 메시징 채널에서는 단순 링크로 대체되거나, \(지원하지 않는 미디어\) 시스템 오류 메시지가 출력됩니다.
{% endhint %}

### 카드형 메시지 \(card\)

![&#xCE74;&#xB4DC;&#xD615; &#xBA54;&#xC2DC;&#xC9C0; &#xC785;&#xB825; &#xD654;&#xBA74;](../../../.gitbook/assets/message-form-card.png)

카드형 메시지에는 **미디어** **썸네일**\(작은 이미지\)이나 **카드에 첨부될 버튼** 등을 정의할 수 있으며, 한 메시지당 최대 9개의 카드를 설정할 수 있습니다.

한 메시지에 두 개 이상의 카드를 설정할 시에는 가로로 스크롤이 가능한 **캐러셀\(Carousel\) 형태**로 표현됩니다. 캐러셀을 지원하지 않는 메신저라면 단일 카드를 여러장 전송하게 되며, 카드 형태의 메시지를 지원하지 않는 메신저에서는 이미지와 텍스트를 별도 전송하게 됩니다.

![&#xCE90;&#xB7EC;&#xC140; &#xBA54;&#xC2DC;&#xC9C0; &#xC608;&#xC2DC; \(&#xCD9C;&#xCC98;: &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xC624;&#xD508;&#xBE4C;&#xB354;\)](../../../.gitbook/assets/image%20%2817%29.png)

![&#xCE74;&#xB4DC;&#xD615; &#xBA54;&#xC2DC;&#xC9C0; &#xC608;&#xC2DC; \(&#xCD9C;&#xCC98;: &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xCE5C;&#xAD6C;&#xD1A1;/&#xC0C1;&#xB2F4;&#xD1A1;\)](../../../.gitbook/assets/userinput_card_message_example.png)

### 위치 메시지 \(location\) 👩🏻‍🔬

![&#xC704;&#xCE58; &#xBA54;&#xC2DC;&#xC9C0; &#xC785;&#xB825; &#xD654;&#xBA74;](../../../.gitbook/assets/message-form-location.png)

위치 응답 방식에서는 설정한 좌표\(위도, 경도\)를 표시하는 지도 형식의 말풍선을 반환합니다.   
위치 메시지를 지원하는 메신저의 경우는 해당 좌표를 가리키는 위치 메시지를, 그 외에는 구글 지도 링크로 대체됩니다.

## 고급 기능

### 메시지 버튼

**텍스트형 메시지**와 **카드형 메시지** 각각의 카드에는 최대 9개의 메시지 버튼을 첨부할 수 있습니다.   
메시지 버튼은 다음 두 가지 유형이 지원됩니다.

* 클릭 시 이동하는 **URL 링크** 
* \*\*\*\*[**포스트백 페이로드 \(Postback payload\)**](response.md#postback-payload) 

메시지 버튼의 동작은 기본적으로 아무런 payload가 설정되지 않은 포스트백 방식이며, 버튼 선택 시 노출되는 팝업 메뉴를 통해 설정을 변경할 수 있습니다. 

![&#xB9D0;&#xD48D;&#xC120; &#xBC84;&#xD2BC; &#xC120;&#xD0DD; &#xC2DC; &#xB178;&#xCD9C;&#xB418;&#xB294; &#xD31D;&#xC5C5; &#xBA54;&#xB274;](../../../.gitbook/assets/message-form-text-buttons.gif)

![&#xB9D0;&#xD48D;&#xC120; &#xBC84;&#xD2BC;&#xC5D0; &#xB9C1;&#xD06C;&#xB97C; &#xC124;&#xC815;&#xD55C; &#xBAA8;&#xC2B5;](../../../.gitbook/assets/message-form-text-button-link.png)

![&#xB9D0;&#xD48D;&#xC120; &#xBC84;&#xD2BC;&#xC5D0; &#xD3EC;&#xC2A4;&#xD2B8;&#xBC31; &#xD398;&#xC774;&#xB85C;&#xB4DC;&#xB97C; &#xC124;&#xC815;&#xD55C; &#xBAA8;&#xC2B5;](../../../.gitbook/assets/message-form-text-button-postback.png)

말풍선 버튼을 입력하는 다른 방법으로 [테이블 데이터 \(스프레드 시트 등\)를 이용하는 방법](request.md#undefined-6)을 참고하세요.

### 포스트백 페이로드 \(Postback Payload\)

텍스트형 메시지나 카드형 메시지의 postback 버튼에 설정하는 payload 기능은 쉽게 이해하기는 어렵지만, **자연스러운 챗봇을 제작하는 핵심 기능**에 해당하니 한번 쯤 읽어보시는 것을 권해드립니다. 

![&#xD3EC;&#xC2A4;&#xD2B8;&#xBC31; &#xD398;&#xC774;&#xB85C;&#xB4DC;&#xB97C; &#xC124;&#xC815;&#xD558;&#xB294; &#xBAA8;&#xC2B5;](../../../.gitbook/assets/message-form-text-button-postback.png)

{% page-ref page="../advanced/postback-payload.md" %}



### 템플릿을 이용한 메시지 생성

앞서 중괄호 \(`{{...}}`\) 를 이용한 텍스트를 발견하고 생소함을 느끼셨나요?   
이 표현은 **템플릿 문법**이라고 불리는 기능으로서, 현재 **대화의 맥락\(Context\)**에 존재하는 값을 이용해 다음 메시지를 생성하는 데 사용할 수 있도록 하는 강력한 기능입니다. 이에 대한 자세한 내용은 다음 문서를 참고해 주세요.

{% page-ref page="../advanced/context.md" %}

{% page-ref page="../advanced/template-syntax.md" %}

### 커스텀 메타데이터 👩🏻‍🔬

![&#xBA54;&#xC2DC;&#xC9C0; &#xC751;&#xB2F5; &#xB178;&#xB4DC; - &#xACE0;&#xAE09; &#xC124;&#xC815;](../../../.gitbook/assets/flow_editor_response_node_advanced.png)

위 속성들은 ![](../../../.gitbook/assets/node-form-advanced-checkbox.png) 를 활성화했을 때 표시되는 설정입니다.

* `meta.custom`
  * CLOSER SDK를 이용하여 Custom UI를 구현하시는 경우 여기에 사용자 정의 데이터를 설정하실 수 있습니다. 여기서 설정된 값은 `message.meta.custom` 을 통해 획득할 수 있습니다. \(최대 1,000자.\)
* `delay`

  * 메시지가 한 번에 전송되는 것을 원치 않은 경우, 메시지 사이에 임의의 지연 시간을 설정할 수 있습니다. \(단위: milliseconds\) 위 스크린샷의 경우에는 1초\(1,000 밀리초\) 뒤에 메시지를 전송합니다. 

