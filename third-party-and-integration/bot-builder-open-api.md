# CLOSER Bot Builder Open API 소개

{% hint style="info" %}
**Bot Builder Open API가 필요하시다면, support@closer.ai로 문의해주세요.**
{% endhint %}

* CLOSER Bot Builder의 Open API입니다.
* CLOSER Webhook과 Bot Builder Open API를 이용하여, 고객 상담용 채팅센터를 개발할 수 있습니다.

## GET /openapi/bot <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/bot"></a>

* CLOSER에서 생성한 챗봇 리스트 가져오기

## GET /openapi/bot/{botId} <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/bot/{botId}"></a>

* 특정 챗봇의 정보 가져오기

## GET /openapi/bot/{botId}/conversation <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/bot/{botId}/conversation"></a>

* 특정 챗봇의 대화 리스트 가져오기

## GET /openapi/bot/{botId}/flow <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/bot/{botId}/flow"></a>

* 특정 챗봇의 플로우 리스트 가져오기

## GET /openapi/conversation/{conversationId} <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/conversation/{conversationId}"></a>

* 특정 대화의 정보 가져오기

## PUT /openapi/conversation/{conversationId} <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-PUT/openapi/conversation/{conversationId}"></a>

* 특정 대화의 정보 업데이트

## PUT /openapi/conversation/{conversationId}/manual <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-PUT/openapi/conversation/{conversationId}/manual"></a>

* 특정 대화의 상담원 연결 상태 업데이트

## GET /openapi/conversation/{conversationId}/manual <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/conversation/{conversationId}/manual"></a>

* 특정 대화의 상담원 연결 상태 가져오기

## GET /openapi/conversation/{conversationId}/message <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/conversation/{conversationId}/message"></a>

* 특정 대화의 메시지 리스트 가져오기

## POST /openapi/conversation/{conversationId}/message <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-POST/openapi/conversation/{conversationId}/message"></a>

* 특정 대화에 메시지 전송하기

## PUT /openapi/conversation/{conversationId}/navigation <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-PUT/openapi/conversation/{conversationId}/navigation"></a>

* 특정 대화의 대화진행 플로우 변경하기

## GET /openapi/conversations <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/conversations"></a>

* 조건에 따라 최종사용자 리스트 가져오기

## GET /openapi/enduser/{id} <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/enduser/{id}"></a>

* 최종사용자의 정보 가져오기

## GET /openapi/endusers <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/endusers"></a>

* 조건에 따라 최종사용자 리스트 가져오기

## POST /openapi/message <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-POST/openapi/message"></a>

* 최종사용자에게 메시지 전송하기

## GET /openapi/messages <a id="CLOSEROpenAPI&#xAC00;&#xC774;&#xB4DC;v0.1-GET/openapi/messages"></a>

* 조건에 따라 메시지리스트 가져오기

