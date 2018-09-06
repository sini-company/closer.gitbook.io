# CLOSER Webhook 연동 가이드

{% hint style="info" %}
**Webhook 연동이 필요하시다면, support@closer.ai로 문의해주세요.**
{% endhint %}

CLOSER에서는 Webhook으로 봇/사용자/상담원의 메시지와 이벤트를 전달합니다.

본 문서에서는 CLOSER에서 전송하는 Webhook을 연동할 수 있도록, Webhook의 포맷과 설정 방법등을 명세합니다.

## Webhook 설정 단계

1. 본 문서에서 명세하는 Webhook의 포맷에 따라, 목적에 맞는 API를 개발하세요.
2. CLOSER Bot에서 개발하신 API의 URL을 등록합니다.
3. CLOSER의 Bot을 사용시 발생하는 이벤트를 개발하신 API로 전송합니다.

## Builder에서 Webhook 전송 설정

![Webhook &#xAD00;&#xB9AC; &#xD654;&#xBA74; &#xC608;&#xC2DC;](../.gitbook/assets/webhook.png)

* Builder &gt; 봇 설정 &gt; Webhook 관리에서 Webhook URL을 등록/수정/삭제 하실 수 있습니다
* 등록하신 Webhook URL이 동작하지 않는 경우 Builder에서 Webhook 전송이 자동으로 비활성화 됩니다

## CLOSER에서 전송하는 Webhook 포맷

### Webhook HTTP Headers

| Key | Value |
| :--- | :--- |
| user-agent | CLOSER/webhook |
| content-type | application/json |

### Webhook POST body Example

#### 일반 {#common}

```yaml
{
 	"id": "00000000-0000-0000-0000-000000000000",
 	"webhookId": "00000000-0000-0000-0000-000000000000",
 	"webhookUrl": "http://your.webhook.com",
 	"messages": [{
 		"sourceId": "Bxxxxx",
 		"data": {
 			"endUser": {
 				"createdAt": "2018-09-04T07:06:53.047Z",
 				"deletedAt": null,
 				"id": "00000000-0000-0000-0000-000000000000",
 				"botId": "Bxxxxx",
 				"lastMessageId": "00000000-0000-0000-0000-000000000000",
 				"params": {
 				},
 				"platform": "web",
 				"userKey": "userKey",
 				"lastConversationId": "00000000-0000-0000-0000-000000000000",
 				"updatedAt": "2018-09-05T06:45:19.087Z"
 			}
 		},
 		"sourceType": "bot",
 		"id": "00000000-0000-0000-0000-000000000000",
 		"event": "bot.end_user.updated",
 		"timestamp": 1536129919092
 	}, {
 		"sourceId": "Bxxxxx",
 		"data": {
 			"conversation": {
 				"endUserId": "00000000-0000-0000-0000-000000000000",
 				"createdAt": "2018-09-05T06:45:19.102Z",
 				"navigation": {},
 				"context": {
 					"navigation": {},
 					"conversationId": "00000000-0000-0000-0000-000000000000",
 					"botId": "Bxxxxx",
 					"params": {
 					},
 					"platform": "web",
 					"userKey": "userKey"
 				},
 				"id": "00000000-0000-0000-0000-000000000000",
 				"botId": "Bxxxxx",
 				"params": {
 				},
 				"userKey": "userKey",
 				"platform": "web",
 				"updatedAt": "2018-09-05T06:45:19.102Z"
 			}
 		},
 		"sourceType": "bot",
 		"id": "00000000-0000-0000-0000-000000000000",
 		"event": "bot.conversation.created",
 		"timestamp": 1536129919116
 	}]
 }
```

#### 상담원 메시지 {#agent-message}

```yaml
{
	"id": "00000000-0000-0000-0000-000000000000",
	"webhookId": "00000000-0000-0000-0000-000000000000",
	"webhookUrl": "http://your.webhook.com",
	"messages": [{
		"sourceId": "Bxxxxx",
		"data": {
			"message": {
				"endUserId": "00000000-0000-0000-0000-000000000000",
				"data": {
					"text": "상담원 메시지",
					"type": "text"
				},
				"requestId": "00000000-0000-0000-0000-000000000000",
				"meta": {
					"sender": {
						"userKey": "Uxxxxx",
						"platform": "closer-chat"
					}
				},
				"conversationId": "00000000-0000-0000-0000-000000000000",
				"id": "00000000-0000-0000-0000-000000000000",
				"isUser": false,
				"timestamp": 1536130434645
			}
		},
		"sourceType": "bot",
		"id": "00000000-0000-0000-0000-000000000000",
		"event": "bot.message.sent",
		"timestamp": 1536130434656
	}]
}
```

#### 봇 메시지 {#bot-message}

```yaml
{
 	"id": "00000000-0000-0000-0000-000000000000",
 	"webhookId": "00000000-0000-0000-0000-000000000000",
 	"webhookUrl": "http://your.webhook.com",
 	"messages": [{
 		"sourceId": "Bxxxxx",
 		"data": {
 			"message": {
 				"endUserId": "00000000-0000-0000-0000-000000000000",
 				"data": {
 					"text": "테스트용 봇 메시지",
 					"type": "text"
 				},
 				"conversationId": "00000000-0000-0000-0000-000000000000",
 				"meta": null,
 				"id": "00000000-0000-0000-0000-000000000000",
 				"isUser": false,
 				"timestamp": 1536129919339
 			}
 		},
 		"sourceType": "bot",
 		"id": "00000000-0000-0000-0000-000000000000",
 		"event": "bot.message.sent",
 		"timestamp": 1536129919373
 	}]
 }
```

#### 고객 메시지 {#user-message}

```yaml
{
 	"id": "00000000-0000-0000-0000-000000000000",
 	"webhookId": "00000000-0000-0000-0000-000000000000",
 	"webhookUrl": "http://your.webhook.com",
 	"messages": [{
 		"sourceId": "Bxxxxx",
 		"data": {
 			"message": {
 				"endUserId": "00000000-0000-0000-0000-000000000000",
 				"data": {
 					"text": "고객 메시지",
 					"type": "text"
 				},
 				"requestId": "00000000-0000-0000-0000-000000000000",
 				"conversationId": "00000000-0000-0000-0000-000000000000",
 				"meta": null,
 				"id": "00000000-0000-0000-0000-000000000000",
 				"isUser": true,
 				"timestamp": 1536130242636
 			}
 		},
 		"sourceType": "bot",
 		"id": "00000000-0000-0000-0000-000000000000",
 		"event": "bot.message.received",
 		"timestamp": 1536130243609
 	}]
 }
```

## Objects

### DELIVERY

| 키 | 타입 | 필수 | 설 |
| :--- | :--- | :--- | :--- |
| id | UUID | Y | Delivery ID |
| webhookId | UUID | Y | Webhook ID |
| webhookUrl | String | Y | Webhook URL |
| messages | Array\(Object\([**EVENT**](closer-webhook.md#event)\)\) | Y | Event 오브젝트의 배열. 일정 시간동안 발생한 이벤트를 배열로 묶어 전달합니다. |

### EVENT

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | UUID | Y | Event ID |
| event | String\([**EVENT\_TYPE**](closer-webhook.md#event_type)\) | Y | Event 구분 |
| sourceType | String\('bot'\) | Y | Event를 발행한 소스 |
| sourceId | String\([**BOT**](closer-webhook.md#bot).id\) | Y | Event 발행한 타입의 아이디. 'bot'인 경 Bot ID |
| timestamp | UNIX Timestamp with milliseconds | Y | Event 발생 시간 |
| data | Object\([**EVENT.DATA**](closer-webhook.md#event-data)\) | Y | Event의 데이터 |

### EVENT.DATA

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| bot | Object\([**BOT**](closer-webhook.md#bot)\) | C | event가 bot인 경우 필수 |
| endUser | Object\([**ENDUSER**](closer-webhook.md#enduser)\) | C | event가 bot.end\_user인 경우 필수 |
| conversation | Object\([**CONVERSATION**](closer-webhook.md#conversation)\) | C | event가 bot.conversation인 경우 필 |
| message | Object\([**MESSAGE**](closer-webhook.md#message)\) | C | event가 bot.message인 경우 필수 |

### BOT

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | String | Y | Bot의 ID |
| title | String | Y | Bot의 이름 |
| description | String | N | Bot의 설명 |
| integration | Object\(BOT.INTEGRATION\) | N | Bot의 연동 정보 |
| preference | Object\(BOT.PREFERENCE\) | N | Bot의 설정 정보 |
| data | Object\(BOT.DATA\) | N | Bot 동작에 필요한 데이터 |
| createdAt | String\(DateTime\) | Y | 생성 날짜 |
| updatedAt | String\(DateTime\) | Y | 업데이트 날짜 |
| deletedAt | String\(DateTime\) | N | 삭제 날짜 |

### ENDUSER

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | UUID | Y | EndUser의 ID |
| botId | String\([**BOT**](closer-webhook.md#bot).id\) | Y | Bot의 ID |
| platform | String\([**PLATFORM\_TYPE**](closer-webhook.md#platform_type)\) | Y | 메신저 타입 |
| userKey | String | Y | 사용자 고유 키값 |
| params | Object\(Dictionary\) | N | 대화에서 사용하는 파라미터 |
| lastMessageId | UUID\([**MESSAGE**](closer-webhook.md#message).id\) | N | 마지막 메시지의 ID |
| lastConversationId | UUID\([**CONVERSATION**](closer-webhook.md#conversation).id\) | N | 마지막 대화의 ID |
| lastConversation | Object\([**CONVERSATION**](closer-webhook.md#conversation)\) | N | 마지막 대화 Object |
| createdAt | String\(DateTime\) | Y | 생성 날짜 |
| updatedAt | String\(DateTime\) | Y | 업데이트 날짜 |
| deletedAt | String\(DateTime\) | N | 삭제 날짜 |

### CONVERSATION

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | UUID | Y | Conversation의 ID |
| botId | String\([**BOT**](closer-webhook.md#bot).id\) | Y | Bot의 ID |
| endUserId | UUID\([**ENDUSER**](closer-webhook.md#enduser).id\) | Y | EndUser의 ID |
| platform | String\([**PLATFORM\_TYPE**](closer-webhook.md#platform_type)\) | Y | 메신저 타입 |
| userKey | String | Y | 사용자의 고유 키값 |
| params | Object\(Dictionary\) | N | 대화에서 사용하는 파라미터 |
| context | Object\([**CONTEXT**](closer-webhook.md#context)\) | N | 대화의 정보 |
| navigation | Object\([**CONTEXT.NAVIGATION**](closer-webhook.md#CLOSERWebChatSDK연동가이드v0.1-CONTEXT.NAVIGATION)\) | N | 대화의 위치 |
| createdAt | String\(DateTime\) | Y | 생성 날짜 |
| updatedAt | String\(DateTime\) | Y | 업데이트 날짜 |

### MESSAGE

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | UUID | Y | Message의 ID |
| endUserId | UUID\([**ENDUSER**](closer-webhook.md#enduser).id\) | Y | EndUser의 ID |
| conversationId | UUID\([**CONVERSATION**](closer-webhook.md#conversation).id\) | Y | Conversation의 ID |
| isUser | Boolean | Y | true인 경우 고객, false인 경우 봇이나 상담원 |
| meta | Object\([**MESSAGE.META**](closer-webhook.md#message-meta)\) | N | 상담원이 경우 meta에 상담원 정보가 포함됨 |
| data | Object\([**MESSAGE.DATA**](closer-webhook.md#message-data)\) | Y | 메시지의 데이터 |
| timestamp | UNIX Timestamp with milliseconds | Y | 메시지 발행 시간 |

### MESSAGE.DATA

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| type | String\([**MESSAGE\_TYPE**](closer-webhook.md#message_type)\) | Y | MESSAGE의 타입 |
| text | String | C | text 타입인 경우 필수 |
| media | Object\([**MESSAGE.DATA.MEDIA**](closer-webhook.md#message-data-media)\) | C | media 타입인 경우 필수 |
| cards | Array\(Object\([**MESSAGE.DATA.CARD**](closer-webhook.md#message-data-card)\)\) | C | cards 타입인 경우 필수 |
| location | Object\([**MESSAGE.DATA.LOCATION**](closer-webhook.md#message-data-location)\) | C | location 타입인 경우 필수 |
| button | Object\([**MESSAGE.DATA.BUTTON**](closer-webhook.md#message-data-button)\) | N | 메시지에 포함된 버튼으로 KEYBOARD.BUTTON과는 형식과 동작이 다름. 링크 삽입 가능 |

### MESSAGE.META

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| sender | Object\([**MESSAGE.META.SENDER**](closer-webhook.md#message-meta-sender)\) | N | 메시지를 전송한 전송자의 정보 |

### MESSAGE.DATA.MEDIA

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| contentType | 'image', 'video', 'audio', 'link' | Y | 이미지, 동영상, 오디오, 링크 |
| uri | String | Y | 이미지, 동영상, 오디오, 링크의 URL |

### MESSAGE.DATA.BUTTON

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| label | String | Y | 버튼 인터페이스에 노출할 이름 |
| uri | String | N | 버튼이 링크로 동작 시 URL, 없으면 키보드 입력 동작 |

### MESSAGE.DATA.CARD

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| title | String | Y | 카드의 제목 |
| description | String | N | 카드의 설명 |
| media | Object\([**MESSAGE.DATA.MEDIA**](closer-webhook.md#message-data-media)\) | N | 카드에 포함될 미디어 |
| uri | String | N | 카드 선택시 이동할 링크 URL |
| buttons | Array\(Object\([**MESSAGE.DATA.BUTTON**](closer-webhook.md#message-data-button)\)\) | N | 카드에 포함된 버튼 리스트 |

### MESSAGE.DATA.LOCATION

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| title | String | N | 위치의 이름 |
| latitude | Number | Y | GPS Latitude |
| longitude | Number | Y | GPS longitude |

### MESSAGE.META.SENDER

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| userKey | String | Y | SENDER 사용 시 필수. 전송자의 ID |
| platform | String | Y | SENDER 사용 시 필수. 전송자의 플랫폼 |

### KEYBOARD {#CLOSERWebChatSDK연동가이드v0.1-KEYBOARD}

* CLOSER의 입력 Object로, 사용자의 입력 타입을 표현합니다.
* text인 경우 사용자는 text를 입력할 수 있고, number인 경우 제약조건을 포함합니다.
* buttons는 사용자의 입력을 button으로 받을 수 있도록 필요한 데이터를 포함합니다.

#### KEYBOARD의 사용자 입력 전송 방식 {#CLOSERWebChatSDK연동가이드v0.1-KEYBOARD의사용자입력전송방식}

* text : 사용자가 입력한 텍스트를 그대로 메시지에 전송합니다.
* buttons : 사용자가 선택한 button의 label의 텍스트를 메시지에 전송합니다.
* number : text와 동일하지만, 조건을 Front에서 검증하도록 개발할 수 있습니다.

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| type | 'text', 'number', 'buttons' | Y | 텍스트, 숫자, 버튼 입력 |
| min | Number | C | number 타입인 경우에 필수, 최소값 |
| max | Number | C | number 타입인 경우에 필수, 최대값 |
| parse | Boolean | N | false인 경우 숫자만 입력 가능, true인 경우 주어진 문자열에서 숫자만 읽어들임 |
| integer | Boolean | N | false인 경우 Integer만 입력 가능 |
| buttons | Array\(Object\([**KEYBOARD.BUTTON**](closer-webhook.md#keyboard-button)\)\) | C | buttons 타입인 경우에 필수 |

### KEYBOARD.BUTTON

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| label | String | Y | 버튼 인터페이스에 노출할 이름 |
| params | Object\(Dictionary\) | N | 버튼 선택 시 저장되는 파라미터. key - value dictionary 타입 |

### CONTEXT

CLOSER에서 대화를 진행하는데 필요한 정보입니다. SDK의 WebChatClient가 Open되면 Context를 message listener에 전송합니다.

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| botId | String | Y | Bot의 ID |
| conversationId | UUID | Y | 대화의 ID. CLOSER에서 자동으로 생성됨 |
| endUserId | UUID | Y | 최종사용자의 ID. CLOSER에서 자동으로 생성됨 |
| navigation | Object\([**CONTEXT.NAVIGATION**](closer-webhook.md#CLOSERWebChatSDK연동가이드v0.1-CONTEXT.NAVIGATION)\) | N | 현재 대화의 위치를 표현하는 오브젝트 |
| params | Object\(Dictionary\) | N | 현재 대화에서 사용하고 있는 파라미터 |
| platform | String\([**PLATFORM\_TYPE**](closer-webhook.md#platform_type)\) | Y | 플랫폼 타입 |
| userKey | String | Y | 최종사용자 식별 키. SDK Open시 주입한 값 |

### CONTEXT.NAVIGATION {#CLOSERWebChatSDK연동가이드v0.1-CONTEXT.NAVIGATION}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| current | Object\([**CONTEXT.NAVIGATION.NODE**](closer-webhook.md#CLOSERWebChatSDK연동가이드v0.1-CONTEXT.NAVIGATION.LASTNODE)\) | Y | 현 노드의 정보 |
| prev | Object\([**CONTEXT.NAVIGATION.NODE**](closer-webhook.md#CLOSERWebChatSDK연동가이드v0.1-CONTEXT.NAVIGATION.LASTNODE)\) | N | 이전 노드의 정보 |

### CONTEXT.NAVIGATION.NODE {#CLOSERWebChatSDK연동가이드v0.1-CONTEXT.NAVIGATION.LASTNODE}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| flowId | Number | Y | 현재 노드의 플로우 ID |
| nodeId | Number | Y | 현재 노드의 ID |
| visitCount | Number | N | 최종사용자가 노드에 방문한 수 |

### AGENT

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | String | Y | 상담원의 User ID |
| profile | Object\([**AGENT.PROFILE**](closer-webhook.md#CLOSERWebChatSDK연동가이드v0.1-AGENT.PROFILE)\) | N | 상담원의 profile 정보 |

### AGENT.PROFILE {#CLOSERWebChatSDK연동가이드v0.1-AGENT.PROFILE}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| displayName | String | N | 상담원의 DisplayName |
| picture | URL | N | 상담원의 프로필 이미지 URL |

## Types

### EVENT\_TYPE

| 타입 | 설명 |
| :--- | :--- |
| bot.updated | Bot의 정보 업데이트 |
| bot.deleted | Bot이 삭제됨 |
| bot.end\_user.created | 새로운 EndUser 생성 |
| bot.end\_user.updated | EndUser의 정보 업데이트 |
| bot.end\_user.deleted | EndUser가 삭제됨\(친구삭제 등\) |
| bot.conversation.created | 새로운 Conversation 생성 |
| bot.conversation.updated | Conversation의 정보 업데이트 |
| bot.conversation.deleted | Conversation이 삭제됨\(대화 만료\) |
| bot.conversation.agent\_call\_requested | 상담원에게 상담 요청 |
| bot.conversation.agent\_call\_connected | 상담 시작 |
| bot.conversation.agent\_call\_cancelled | 상담원에게 상담요청을 고객이 취소 |
| bot.conversation.agent\_call\_disconnected | 상담 종료 |
| bot.message.sent | 메시지 전송\(봇, 상담원\) |
| bot.message.received | 메시지 수신\(사용자\) |

### PLATFORM\_TYPE

| 타입 | 설명 |
| :--- | :--- |
| kakao | 카카오톡 스마트 API |
| kakaobiz | 카카오 상담톡 |
| facebook | 페이스북 메신저 |
| line | 라인 |
| navertalk | 네이버톡톡 |
| bizchat | SMS 문자 메시지 채팅 BizChat |
| wechat | 위챗 |
| web | 웹챗 |
| test | 테스트용 챗 |

### MESSAGE\_TYPE

| 타입 | 설명 |
| :--- | :--- |
| text |  텍스트 메시지 |
| media | 이미지, 동영상, 오디오 등의 미디어 |
| cards | 카드 타입 리스트 \(Carousel로 사용\) |
| location | 위치 정보 \(latitude, longitude\) |



