---
description: CLOSER에서 사용되는 챗봇의 응답과 요청에 대한 개념을 알아봅니다.
---

# 응답과 요청

CLOSER에서는 여러 메시징 채널에서 사용되는 챗봇의 응답과 요청에 대한 구성요소들을 효율적으로 표현할 수 있도록 공통적인는 응답 메시지 유형과 요청 방식들을 별도로 정의하여 사용하고 있습니다. 

이번 페이지에서 다루는 응답 유형과 요청 유형은 대부분의 메시징 채널에서 적합하게 변환될 것이며, 대부분의 메시징 채널에서 전달받은 메시지 또한 CLOSER에서 사용하고 있는 응답과 요청 형식에 알맞게 변환될 것입니다.

각 메시징 채널 별 지원 여부에 대해서는 [메신저 연동 &gt; 지원 여부 테이블](../messenger-integrations/#availability-table) 문서를 확인해주세요.

## 응답 유형

### 텍스트 메시지 \(Text Message\)

![&#xD14D;&#xC2A4;&#xD2B8; &#xBA54;&#xC2DC;&#xC9C0; &#xC608;&#xC2DC; \(&#xCD9C;&#xCC98;: &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xC624;&#xD508;&#xBE4C;&#xB354; &#xB3C4;&#xC6C0;&#xB9D0;\) ](../../.gitbook/assets/image%20%286%29.png)

* type: `text`
* 텍스트로 이루어진 일반적인 말풍선 메시지입니다. 모든 메시징 채널에서 지원합니다.
* CLOSER에서는 텍스트 메시지에 버튼을 첨부할 수 있는데, 이 기능의 지원 여부는 메시징 채널에 따라 다릅니다.

### 미디어 메시지 \(Media Message\)

![&#xBBF8;&#xB514;&#xC5B4; &#xBA54;&#xC2DC;&#xC9C0; &#xC608;&#xC2DC; \(&#xCD9C;&#xCC98;: &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xC624;&#xD508;&#xBE4C;&#xB354; &#xB3C4;&#xC6C0;&#xB9D0;\)](../../.gitbook/assets/image%20%2814%29.png)

* type: `media`
* 사진이나 동영상 등의 미디어를 포함한 메시지입니다. 메시징 채널별로 지원 여부와 제약사항이 다릅니다.
* 만약 사진과 함께 메시지나 링크/버튼 등을 함께 첨부하고자 하실 경우에는 **카드형 메시지** 항목을 참고해 주세요.

### 카드형 메시지 \(Card Message\)

![&#xCE74;&#xB4DC;&#xD615; &#xBA54;&#xC2DC;&#xC9C0; &#xC608;&#xC2DC; 1 \(&#xCD9C;&#xCC98;: &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xC624;&#xD508;&#xBE4C;&#xB354; &#xB3C4;&#xC6C0;&#xB9D0;\)](../../.gitbook/assets/image%20%282%29.png)

![&#xCE74;&#xB4DC;&#xD615; &#xBA54;&#xC2DC;&#xC9C0; &#xC608;&#xC2DC; 2 \(&#xCD9C;&#xCC98;: &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xC624;&#xD508;&#xBE4C;&#xB354; &#xB3C4;&#xC6C0;&#xB9D0;\)](../../.gitbook/assets/image%20%2838%29.png)

* type: `cards`
* 사진이나 동영상과 함께 텍스트나 버튼 등 말풍선 안에 풍부한\(rich\) 컨텐츠를 보유한 메시지입니다.
* 한 메시지에 하나 이상의 카드를 첨부할 수 있습니다. 
* 두 개 이상의 카드가 첨부된 경우 메시징 채널에 따라 가로로 슬라이드가 가능한 캐러셀\(carousel\) 형태로 표시되거나 여러 장의 카드를 연속하여 전송합니다.

### 위치 메시지 \(Location Message\) 👩🏻‍🔬

![&#xC704;&#xCE58; &#xBA54;&#xC2DC;&#xC9C0; &#xC608;&#xC2DC; \(&#xCD9C;&#xCC98;: &#xD398;&#xC774;&#xC2A4;&#xBD81; &#xB274;&#xC2A4;&#xB8F8;\)](../../.gitbook/assets/image%20%2831%29.png)

* type: `location`
* 위도와 경도를 첨부하여 지도상에 위치를 표시하는 메시지입니다. 경우에 따라 위치에 이름을 지정할수도 있습니다.
* 메시징 채널에 따라 지원 여부가 다릅니다.

## 요청 유형

### 일반 요청 \(Generic Request\)

![&#xC77C;&#xBC18; &#xC785;&#xB825; &#xBC29;&#xC2DD; \(&#xD398;&#xC774;&#xC2A4;&#xBD81; &#xBA54;&#xC2E0;&#xC800;\)](../../.gitbook/assets/image%20%2846%29.png)

사용자의 메시지 입력을 대기하는 일반적인 요청 방식입니다.  
사용자는 텍스트를 비롯하여 이미지나 위치 메신저에서 지원하는 다양한 입력 방식을 통해 챗봇에게 메시지를 전송할 수 있습니다.

### 포스트백 버튼 \(Postback Button\)

![&#xD3EC;&#xC2A4;&#xD2B8;&#xBC31; &#xBC84;&#xD2BC; &#xC608;&#xC2DC; \(&#xCD9C;&#xCC98;: &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xC624;&#xD508;&#xBE4C;&#xB354; &#xB3C4;&#xC6C0;&#xB9D0;\)](../../.gitbook/assets/image%20%2838%29.png)

텍스트형 메시지나 카드형 메시지에는 하나 이상의 버튼을 첨부할 수 있습니다. 여기서 버튼 클릭 시 특정 링크\(URL\)로 이동하는 것이 아닌, 사용자로 하여금 챗봇에게 메시지를 전송하도록 설정할수도 있습니다. 이 기능을 포스트백이라고 부릅니다. \(위 예시에서는 "한 개 담기" 버튼이 포스트백 버튼에 해당합니다.\)

포스트백 버튼에서는 사용자 정의 데이터를 첨부할 수 있는데, 이 기능을 [**포스트백 페이로드\(Postback Payload\)**](advanced/postback-payload.md) 라고 합니다. 이 기능은 동일한 텍스트의 버튼들에서 어떤 버튼을 눌렀는지 구분할 수 있게끔 도와주며, 나아가 대화의 맥락을 벗어난 경우에도 포스트백 페이로드를 통해 전달된 값을를 이용하여 사용자가 의도한 시나리오에 접근할 수 있도록 도와줍니다.

포스트백 페이로드 기능의 지원 여부는 메시징 채널에 따라 다릅니다.

### 빠른 답장 \(Quick Reply\)

![&#xBE60;&#xB978; &#xB2F5;&#xC7A5; &#xC608;&#xC2DC; \(&#xCD9C;&#xCC98;: &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xC624;&#xD508;&#xBE4C;&#xB354; &#xB3C4;&#xC6C0;&#xB9D0;\)](../../.gitbook/assets/image%20%2851%29.png)

빠른 답장은 입력 창 또는 말풍선 아래에 타원형의 칩 \(Chip\) 형태로 노출되는 버튼으로서, 해당 버튼을 클릭하면 버튼에 해당하는 메시지를 전송하는 기능입니다. 주로 선택지형 입력이 필요 할 때 사용됩니다.

빠른 답장 버튼에도 [**포스트백 페이로드 기능**](advanced/postback-payload.md)을 이용할 수 있습니다.

## 더 알아보기

여기서 배운 응답과 요청 유형은 각각 메시지 응답 노드와 사용자 입력 요청 노드를 통해 이용할 수 있습니다.  
해당 노드의 이용 방법은 다음 페이지에서 알아보세요.

{% page-ref page="node/response.md" %}

{% page-ref page="node/request.md" %}
