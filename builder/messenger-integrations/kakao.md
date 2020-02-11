---
description: 챗봇을 카카오톡 플러스친구에 연동하는 방법을 안내합니다.
---

# 카카오톡 연동

## 시작하기 전에    <a id="announcement"></a>

카카오톡채널 계정에 챗봇을 연동하는 방법은 두 가지가 있습니다.

* 카카오 i 오픈빌더 \(현재\)
* API형 스마트채팅 \(레거시, **신규가입 불가**\)

API형 스마트채팅은 기존 플러스친구 사용자에게 제공되던 방식으로 2018년 12월 3일 신규 가입이 중단되었습니다. 해당 서비스는 기존 사용자들에 한해서만 19년 12월까지 제공되며, 이후에는 완전히 종료됩니다.

> API형 스마트채팅 신규 등록 중단 안내  
> [https://center-pf.kakao.com/notices/233](https://center-pf.kakao.com/notices/233)

{% hint style="info" %}
기존 API형 스마트채팅을 카카오 i 오픈빌더로 전환하고 싶으신가요? 아래 서비스를 이용해 보세요!  
[https://kakao.closer.ai](https://kakao.closer.ai)
{% endhint %}

## 요구사항  <a id="prerequisite"></a>

활성화된 카카오톡 플러스친구 계정이 필요합니다.  
카카오톡 플러스친구 서비스는 비지니스를 위한 카카오톡 계정 생성 서비스로서, 1:1 채팅이나 마케팅 메시지 전송 등 비즈니스에 필요한 기능들을 제공합니다. 플러스친구 계정을 생성하려면 아래 카카오 for 비즈니스 홈페이지를 이용해 주세요.

* 카카오 for 비즈니스 홈페이지: [https://business.kakao.com/](https://business.kakao.com/)
* 카카오톡 플러스친구 FAQ: [https://cs.kakao.com/helps?category=29&locale=ko&service=8](https://cs.kakao.com/helps?category=29&locale=ko&service=8)

## 카카오 i 오픈빌더 연동    <a id="openbuilder"></a>

{% hint style="info" %}
별도 문의 바랍니다.  
\([support@closer.ai](mailto:support@closer.ai?subject=카카오톡%20오픈빌더%20연동%20문의)\)
{% endhint %}

## API형 스마트채팅 연동 <a id="smartchat"></a>

플러스친구 스마트채팅은 사용자의 메시지에 대해 정해진 답변을 제공하거나, API를 통해 답변을 생성할 수 있습니다. CLOSER에서는 API형 스마트채팅을 통 챗봇 연동을 제공합니다.

* 카카오톡 스마트채팅 FAQ: [https://cs.kakao.com/helps?category=285&locale=ko&service=102](https://cs.kakao.com/helps?category=285&locale=ko&service=102)
* API형 스마트채팅 연동 가이드: [https://github.com/plusfriend/auto\_reply](https://github.com/plusfriend/auto_reply)

{% hint style="warning" %}
API형 스마트채팅 서비스는 2018년 12월 3일 이후 신규 가입이 중단됩니다.  
기존에 등록한 사용자들에 한해 2019년 12월까지만 서비스가 제공되며, 이후에는 서비스가 종료됩니다.

새롭게 카카오톡 플러스친구에 챗봇을 연결하시려는 경우 카카오 i 오픈빌더 연동 방법을 이용하세요.
{% endhint %}

### 1. 스마트채팅 연동 설정

플러스친구 관리자 센터로 진입하여 보유하신 플러스친구 프로필을 선택합니다.

![&#xD50C;&#xB7EC;&#xC2A4;&#xCE5C;&#xAD6C; &#xAD00;&#xB9AC;&#xC790;&#xC13C;&#xD130; &#xD504;&#xB85C;&#xD544; &#xCD08;&#xAE30; &#xD654;&#xBA74;](../../.gitbook/assets/kakao_smartchat_1.png)

화면 좌측 스마트채팅 메뉴를 클릭해 스마트채팅 설정 화면으로 진입합니다.

![&#xD50C;&#xB7EC;&#xC2A4;&#xCE5C;&#xAD6C; &#xAD00;&#xB9AC;&#xC790;&#xC13C;&#xD130; &#xC2A4;&#xB9C8;&#xD2B8;&#xCC44;&#xD305; &#xC124;&#xC815; &#xD654;&#xBA74;](../../.gitbook/assets/kakao_smartchat_5.png)

스마트채팅 설정 화면 우측의 API형 스마트채팅 하단에 있는 **설정하기** \(기존 설정이 존재하는 경우 ✏️ 아이콘\) 버튼을 클릭하여 API형 스마트채팅 설정 메뉴로 진입합니다.

![&#xD50C;&#xB7EC;&#xC2A4;&#xCE5C;&#xAD6C; &#xAD00;&#xB9AC;&#xC790;&#xC13C;&#xD130; API&#xD615; &#xC2A4;&#xB9C8;&#xD2B8;&#xCC44;&#xD305; &#xC124;&#xC815; &#xD654;&#xBA74; ](../../.gitbook/assets/kakao_smartchat_3.png)

API형 스마트채팅 설정 화면으로 들어오셨다면, 아래 항목을 입력해주세요.

* **앱 URL**: CLOSER에서 제공한 API URL을 입력하세요.
* **알림받을 전화번호**: 챗봇 동작의 오류나 프로필 이용 정지 등의 알림을 수신할 전화번호를 설정합니다. 전화번호를 설정하지 않으면 API형 스마트채팅을 시작할 수 없습니다.
* 앱 이름과 앱 설명에는 원하시는 내용을 입력하세요. CLOSER 챗봇 동작과는 관계가 없습니다.

앱 URL 입력 후 **API 테스트** 버튼을 눌러 응답을 확인해 보세요. 연동이 제대로 이루어 진 경우 아래와 같이 테스트 결과가 출력됩니다.

![&#xD50C;&#xB7EC;&#xC2A4;&#xCE5C;&#xAD6C; &#xAD00;&#xB9AC;&#xC790;&#xC13C;&#xD130; API&#xD615; &#xC2A4;&#xB9C8;&#xD2B8;&#xCC44;&#xD305; &#xC124;&#xC815; &#xD654;&#xBA74; - API &#xD14C;&#xC2A4;&#xD2B8; &#xACB0;&#xACFC;](../../.gitbook/assets/kakao_smartchat_4.png)

API 응답을 확인하였으면 아래 **저장하기** 버튼을 클릭해 설정을 저장해 주세요.

### 2. 스마트채팅 연동 테스트

![&#xD50C;&#xB7EC;&#xC2A4;&#xCE5C;&#xAD6C; &#xAD00;&#xB9AC;&#xC790;&#xC13C;&#xD130; &#xC2A4;&#xB9C8;&#xD2B8;&#xCC44;&#xD305; &#xC124;&#xC815; &#xD654;&#xBA74; \(&#xC5F0;&#xB3D9; &#xC124;&#xC815; &#xD6C4;\) ](../../.gitbook/assets/kakao_smartchat_2.png)

이제 스마트채팅 설정 화면으로 돌아가 **시작하기** 버튼을 클릭해 주세요.  
연동이 잘 이루어진 경우 플러스친구 1:1 대화창을 통해 챗봇 동작을 확인할 수 있습니다.



## 상담 연계 <a id="live-chat-integration"></a>

카카오톡에서의 상담은 ① 카카오톡채널 관리자센터의 1:1 채팅 기능과 ② 카카오톡 상담톡을 이용하는 두 가지 방식이 존재합니다.

### 카카오톡채널 1:1 채팅

![&#xCE74;&#xCE74;&#xC624;&#xD1A1;&#xCC44;&#xB110; &#xAD00;&#xB9AC;&#xC790;&#xC13C;&#xD130; &amp;gt; 1:1&#xCC44;&#xD305; &#xC124;&#xC815;](../../.gitbook/assets/manual_response_kakao_center-pf.png)

> [ht](https://business.kakao.com/dashboard)[tps://business.kakao.com/dashboard](https://business.kakao.com/dashboard)

카카오톡채널 1:1채팅은 카카오톡채널 관리자센터에서 제공하는 1:1 대화 기능으로, 위 설정 페이지에서 1:1채팅을 사용 설정하시면 고객이 언제든 챗봇에서 1:1채팅으로 전환하여 대화를 시작할 수 있습니다.

{% hint style="danger" %}
카카오톡채널 1:1채팅을 통해 주고받은 메시지는 카카오톡 외부로 제공되지 않습니다.  
따라서 **CLOSER에서 대화를 확인하실 수 없으며**, [**CLOSER Chat**](../../chat/about/)**을 통한 상담도 불가능**합니다.
{% endhint %}

### 카카오톡 상담톡

> [https://business.kakao.com/info/bizmessage/](https://business.kakao.com/info/bizmessage/)

카카오톡 상담톡은 카카오톡에서 기업 대상으로 판매하는 고객센터 구축용 상품으로, 상담톡에 가입하여 이용하시면 [CLOSER Chat](../../chat/about/)을 통한 상담을 진행하실 수 있습니다.

CLOSER는 현재 루나소프트와 협업하여 상담톡을 제공해드리고 있습니다.   
상담톡 신규 가입을 희망하신다면 아래 메일 주소로 상담톡 도입 문의를 남겨주세요.

{% hint style="info" %}
상담톡 도입 문의는 아래 메일 주소로 보내주세요.  
[support@closer.ai](mailto:support@closer.ai?subject=%5B%EC%B9%B4%EC%B9%B4%EC%98%A4%EC%83%81%EB%8B%B4%ED%86%A1%EC%8B%A0%EC%B2%AD%5D%20%ED%9A%8C%EC%82%AC%EB%AA%85&body=-%20%EA%B3%A0%EA%B0%9D%EC%82%AC%EB%AA%85%20%3A%0A-%20%EB%B0%9C%EC%8B%A0%ED%94%84%EB%A1%9C%ED%95%84%EB%AA%85%20%3A%0A-%20%EA%B3%A0%EA%B0%9D%EC%82%AC%20%EB%8C%80%ED%91%9C%EB%B2%88%ED%98%B8%20%3A%0A-%20%EA%B3%A0%EA%B0%9D%EC%82%AC%20%ED%99%88%ED%8E%98%EC%9D%B4%EC%A7%80%20URL%20%3A%0A-%20%EC%82%AC%EC%97%85%EC%9E%90%EB%93%B1%EB%A1%9D%EC%A6%9D%20%3A%20%28%EC%B2%A8%EB%B6%80%29)
{% endhint %}

