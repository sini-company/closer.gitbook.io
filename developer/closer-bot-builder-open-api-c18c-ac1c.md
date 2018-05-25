## CLOSER Bot Builder Open API {#CLOSEROpenAPI가이드v0.1-CLOSERBotBuilderOpenAPI}

* CLOSER Bot Builder의 Open API입니다.
* CLOSER Webhook과 Bot Builder Open API를 이용하여, 고객 상담용 채팅센터를 개발할 수 있습니다.

### GET /openapi/bot {#CLOSEROpenAPI가이드v0.1-GET/openapi/bot}

* CLOSER에서 생성한 챗봇 리스트 가져오기

### GET /openapi/bot/{botId} {#CLOSEROpenAPI가이드v0.1-GET/openapi/bot/{botId}}

* 특정 챗봇의 정보 가져오기

### GET /openapi/bot/{botId}/conversation {#CLOSEROpenAPI가이드v0.1-GET/openapi/bot/{botId}/conversation}

* 특정 챗봇의 대화 리스트 가져오기

### GET /openapi/bot/{botId}/flow {#CLOSEROpenAPI가이드v0.1-GET/openapi/bot/{botId}/flow}

* 특정 챗봇의 플로우 리스트 가져오기

### GET /openapi/conversation/{conversationId} {#CLOSEROpenAPI가이드v0.1-GET/openapi/conversation/{conversationId}}

* 특정 대화의 정보 가져오기

### PUT /openapi/conversation/{conversationId} {#CLOSEROpenAPI가이드v0.1-PUT/openapi/conversation/{conversationId}}

* 특정 대화의 정보 업데이트

### PUT /openapi/conversation/{conversationId}/manual {#CLOSEROpenAPI가이드v0.1-PUT/openapi/conversation/{conversationId}/manual}

* 특정 대화의 상담원 연결 상태 업데이트

### GET /openapi/conversation/{conversationId}/manual {#CLOSEROpenAPI가이드v0.1-GET/openapi/conversation/{conversationId}/manual}

* 특정 대화의 상담원 연결 상태 가져오기

### GET /openapi/conversation/{conversationId}/message {#CLOSEROpenAPI가이드v0.1-GET/openapi/conversation/{conversationId}/message}

* 특정 대화의 메시지 리스트 가져오기

### POST /openapi/conversation/{conversationId}/message {#CLOSEROpenAPI가이드v0.1-POST/openapi/conversation/{conversationId}/message}

* 특정 대화에 메시지 전송하기

### PUT /openapi/conversation/{conversationId}/navigation {#CLOSEROpenAPI가이드v0.1-PUT/openapi/conversation/{conversationId}/navigation}

* 특정 대화의 대화진행 플로우 변경하기

### GET /openapi/conversations {#CLOSEROpenAPI가이드v0.1-GET/openapi/conversations}

* 조건에 따라 최종사용자 리스트 가져오기

### GET /openapi/enduser/{id} {#CLOSEROpenAPI가이드v0.1-GET/openapi/enduser/{id}}

* 최종사용자의 정보 가져오기

### GET /openapi/endusers {#CLOSEROpenAPI가이드v0.1-GET/openapi/endusers}

* 조건에 따라 최종사용자 리스트 가져오기

### POST /openapi/message {#CLOSEROpenAPI가이드v0.1-POST/openapi/message}

* 최종사용자에게 메시지 전송하기

### GET /openapi/messages {#CLOSEROpenAPI가이드v0.1-GET/openapi/messages}

* 조건에 따라 메시지리스트 가져오기



