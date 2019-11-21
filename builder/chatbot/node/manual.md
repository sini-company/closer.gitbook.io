---
description: 챗봇의 자동응답을 일시 중지하고 상담원을 호출하는 기능을 제공합니다.
---

# 상담원 호출 노드

![&#xC0C1;&#xB2F4;&#xC6D0; &#xD638;&#xCD9C; &#xB178;&#xB4DC; &#xC124;&#xC815; &#xD654;&#xBA74;](../../../.gitbook/assets/agent-call-node-form.png)

상담원 호출 노드는 [CLOSER Chat](../../../chat/about/)이나 다른 고객센터 솔루션과 연동할 경우 상담원을 호출 이벤트를 발생시키는 노드 입니다. 

* 해당 노드에 진입하면 안내메시지를 출력한 뒤 상담원을 호출하는 webhook이 전송됩니다.
* 상담원이 상담을 종료하거나 사용자가 취소 메시지를 입력하기 전까지 챗봇의 자동응답은 일시 중지됩니다.

{% hint style="info" %}
봇 편집기의 **대화 테스트** 에서는 상담원 호출 기능을 이용하실 수 없습니다.
{% endhint %}

## 카카오톡

![&#xC0C1;&#xB2F4;&#xC6D0; &#xD638;&#xCD9C; &#xB178;&#xB4DC; &#xC124;&#xC815; &amp;gt; &#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xC124;&#xC815; \(data.message.kakao\)](../../../.gitbook/assets/manual_response_node_kakao.png)

카카오톡의 경우에는 상담원 호출 노드에 진입 시 상담원을 즉시 호출하지 않고, 추가적으로 **상담원 연결** 버튼을 누르도록 새로운 메시지를 반환합니다. 이는 카카오톡 오픈빌더에서 [메시지 버튼으로만 상담원 연결 기능을 제공](https://i.kakao.com/docs/key-concepts-plugin#%EC%83%81%EB%8B%B4%EC%9B%90-%EC%97%B0%EA%B2%B0https://i.kakao.com/docs/key-concepts-plugin#%EC%83%81%EB%8B%B4%EC%9B%90-%EC%97%B0%EA%B2%B0)하기 때문인데요, 이 때 사용될 메시지를 `data.message.kakao` 값을 통해 편집하실 수 있습니다. 

![&#xCE74;&#xCE74;&#xC624;&#xD1A1; &#xBA54;&#xC2DC;&#xC9C0; &#xC124;&#xC815; &#xACB0;&#xACFC;](../../../.gitbook/assets/manual_response_node_kakao_result.jpg)

카카오톡에서의 상담은 ① 카카오톡채널 관리자센터의 1:1 채팅 기능과 ② 카카오톡 상담톡을 이용하는 두 가지 방식이 존재합니다.

### 카카오톡채널 1:1 채팅

![&#xCE74;&#xCE74;&#xC624;&#xD1A1;&#xCC44;&#xB110; &#xAD00;&#xB9AC;&#xC790;&#xC13C;&#xD130; &amp;gt; 1:1&#xCC44;&#xD305; &#xC124;&#xC815;](../../../.gitbook/assets/manual_response_kakao_center-pf.png)

> [ht](https://business.kakao.com/dashboard)[tps://business.kakao.com/dashboard](https://business.kakao.com/dashboard)

카카오톡채널 1:1채팅은 카카오톡채널 관리자센터에서 제공하는 1:1 대화 기능으로, 위 설정 페이지에서 1:1채팅을 사용 설정하시면 고객이 언제든 챗봇에서 1:1채팅으로 전환하여 대화를 시작할 수 있습니다.

{% hint style="danger" %}
카카오톡채널 1:1채팅을 통해 주고받은 메시지는 외부 고객사로 제공되지 않습니다.  
따라서 **CLOSER에서 대화를 확인하실 수 없으며**, [**CLOSER Chat**](../../../chat/about/)**을 통한 상담도 불가능**합니다.
{% endhint %}

### 카카오톡 상담톡

> [https://business.kakao.com/info/bizmessage/](https://business.kakao.com/info/bizmessage/)

카카오톡 상담톡은 카카오톡에서 기업 대상으로 판매하는 고객센터 구축용 상품으로, 상담톡을 이용하시게 되면 [CLOSER Chat](../../../chat/about/)을 통해 상담을 진행하실 수 있습니다.

CLOSER는 현재 루나소프트와 협업하여 상담톡을 제공해드리고 있습니다.   
상담톡 신규 가입을 희망하신다면 아래 메일 주소로 상담톡 도입 문의를 남겨주세요.

{% hint style="info" %}
상담톡 도입 문의는 아래 메일 주소로 보내주세요.  
[support@closer.ai](mailto:support@closer.ai?subject=%5B%EC%B9%B4%EC%B9%B4%EC%98%A4%EC%83%81%EB%8B%B4%ED%86%A1%EC%8B%A0%EC%B2%AD%5D%20%ED%9A%8C%EC%82%AC%EB%AA%85&body=-%20%EA%B3%A0%EA%B0%9D%EC%82%AC%EB%AA%85%20%3A%0A-%20%EB%B0%9C%EC%8B%A0%ED%94%84%EB%A1%9C%ED%95%84%EB%AA%85%20%3A%0A-%20%EA%B3%A0%EA%B0%9D%EC%82%AC%20%EB%8C%80%ED%91%9C%EB%B2%88%ED%98%B8%20%3A%0A-%20%EA%B3%A0%EA%B0%9D%EC%82%AC%20%ED%99%88%ED%8E%98%EC%9D%B4%EC%A7%80%20URL%20%3A%0A-%20%EC%82%AC%EC%97%85%EC%9E%90%EB%93%B1%EB%A1%9D%EC%A6%9D%20%3A%20%28%EC%B2%A8%EB%B6%80%29)
{% endhint %}

