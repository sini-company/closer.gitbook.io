---
description: CLOSER 실시간 웹 채팅의 UI를 직접 개발할 수 있는 Webchat SDK에 대해 소개합니다.
---

# CLOSER Webchat SDK 연동 가이드

{% hint style="info" %}
**Webchat SDK 이용이 필요하시다면 support@closer.ai로 문의주세요.**
{% endhint %}

## WebChat SDK 초기화 <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-WebChatSDK&#xCD08;&#xAE30;&#xD654;"></a>

* apiKey : 필수, CLOSER에서 제공하는 API 접근 키

```javascript
var webchatSDK = new CloserSDK.WebChat({
  apiKey: '{closer-api-token}'
});
```

## WebChatClient 생성 <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-WebChatClient&#xC0DD;&#xC131;"></a>

* userKey : 선택, 기본값으로 browser fingerprint 사용, 최종사용자의 고유 ID로 String 타입
* botId : 필수, CLOSER에서 생성한 Bot의 ID
* params : 선택, 초기 파라미터 주입

```javascript
var wsClient = webchatSDK.open({
  userKey: '{closer-enduser-key}',
  botId: '{botId}',
  params: {}
});
```

## Open / Close / Message Listener 추가 / 제거 <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-Open/Close/MessageListener&#xCD94;&#xAC00;/&#xC81C;&#xAC70;"></a>

```javascript
var onOpen = function() {};
var onClose = function() {};
var onError = function(error) {};
var onMessage = function(data) {};

// Add Listener
wsClient.addListener('message', onMessage);
wsClient.addListener('open', onOpen);
wsClient.addListener('error', onError);
wsClient.addListener('close', onClose);

// Remove Listener
wsClient.removeListener('message', onMessage);
wsClient.removeListener('open', onOpen);
wsClient.removeListener('error', onError);
wsClient.removeListener('close', onClose);
```

## 메시지 전송 \(high-level\) <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-&#xBA54;&#xC2DC;&#xC9C0;&#xC804;&#xC1A1;(high-level)"></a>

```javascript
// Text type message
wsClient.sendMessage({
  type: 'text',
  text: 'message'
});

// Media type message
wsClient.sendMessage({
  type: 'media',
  media: { contentType: 'image', uri: 'http://...' }
});
```

## 메시지 전송 \(low-level\) <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-&#xBA54;&#xC2DC;&#xC9C0;&#xC804;&#xC1A1;(low-level)"></a>

```javascript
// Text type message
wsClient.send({
  message: {
    data: {
      type: 'text',
      text: 'message'
    },
    timestamp: new Date()
  }
});

// Media type message
wsClient.send({
  message: {
    data: {
      type: 'media',
      media: { contentType: 'image', uri: 'http://...' }
    }
  }
});
```

## Objects

### MESSAGE <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-MESSAGE"></a>

CLOSER 메시지 Object로 메시지 송/수신에 사용됩니다.

메시지 전송시에는 text / media / location 전송만 지원합니다.

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | String | N | 메시지의 ID. CLOSER에서 자동으로 생성됨 |
| endUserId | UUID | N | 최종사용자의 ID. CLOSER에서 자동으로 생성됨 |
| conversationId | UUID | N | 대화의 ID. CLOSER에서 자동으로 생성됨 |
| data | Object\(MESSAGE.DATA\) | Y | 메시지의 데이터. MESSAGE.DATA 참고 |
| meta | Object\(MESSAGE.META\) | N | 메시지의  메타데이터. MESSAGE.META 참고 |
| isUser | Boolean | N | 최종사용자인 경우 true, 그 외에는 false |
| timestamp | UNIX Timestamp with milliseconds | N | 메시지 발행 시간 |

### MESSAGE.DATA

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| type | 'text', 'media', 'cards', 'location' | Y | 메시지의 타입. text : 텍스트 메시지, media : 이미지, 동영상, 오디오 등의 미디어, cards : 카드 타입 리스트 \(Carousel로 사용\), location: 위치 정보 \(latitude, longitude\) |
| text | String | C | text 타입인 경우 필수 |
| media | Object\(MESSAGE.DATA.MEDIA\) | C | media 타입인 경우 필수 |
| cards | Array\(Object\(MESSAGE.DATA.CARD\)\) | C | cards 타입인 경우 필수 |
| location | Object\(MESSAGE.DATA.LOCATION\) | C | location 타입인 경우 필수 |
| button | Object\(MESSAGE.DATA.BUTTON\) | N | 메시지에 포함된 버튼으로 KEYBOARD.BUTTON과는 형식과 동작이 다름 링크 삽입 가능 |

### MESSAGE.META

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| sender | Object\(MESSAGE.META.SENDER\) | N | 메시지를 전송한 전송자의 정보 |

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
| media | Object\(MESSAGE.DATA.MEDIA\) | N | 카드에 포함될 미디어 |
| uri | String | N | 카드 선택시 이동할 링크 URL |
| buttons | Array\(Object\(MESSAGE.DATA.BUTTON\)\) | N | 카드에 포함된 버튼 리스트 |

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

### KEYBOARD <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-KEYBOARD"></a>

* CLOSER의 입력 Object로, 사용자의 입력 타입을 표현합니다.
* text인 경우 사용자는 text를 입력할 수 있고, number인 경우 제약조건을 포함합니다.
* buttons는 사용자의 입력을 button으로 받을 수 있도록 필요한 데이터를 포함합니다.

#### KEYBOARD의 사용자 입력 전송 방식 <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-KEYBOARD&#xC758;&#xC0AC;&#xC6A9;&#xC790;&#xC785;&#xB825;&#xC804;&#xC1A1;&#xBC29;&#xC2DD;"></a>

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
| buttons | Array\(Object\(KEYBOARD.BUTTON\)\) | C | buttons 타입인 경우에 필수 |

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
| navigation | Object\(CONTEXT.NAVIGATION\) | N | 현재 시나리오의 위치를 표현하는 오브젝트 |
| params | Object\(Dictionary\) | N | 현재 시나리오에서 사용중인 파라미터 |
| platform | 'web' | Y | 사용자 메시징 채널 |
| userKey | String | Y | 사용자 식별 키 |

### CONTEXT.NAVIGATION <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-CONTEXT.NAVIGATION"></a>

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| current | Object\(CONTEXT.NAVIGATION.NODE\) | Y | 마지막 노드의 정보 |
| prev | Object\(CONTEXT.NAVIGATION.NODE\) | N | 이전 노드의 정보 |

### CONTEXT.NAVIGATION.NODE <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-CONTEXT.NAVIGATION.LASTNODE"></a>

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| flowId | Number | Y | 현재 노드의 플로우 ID |
| nodeId | Number | Y | 현재 노드의 ID |

### AGENT

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | String | Y | 상담원의 User ID |
| profile | Object\(AGENT.PROFILE\) | N | 상담원의 profile 정보 |

### AGENT.PROFILE <a id="CLOSERWebChatSDK&#xC5F0;&#xB3D9;&#xAC00;&#xC774;&#xB4DC;v0.1-AGENT.PROFILE"></a>

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| displayName | String | N | 상담원의 DisplayName |
| picture | String\(URL\) | N | 상담원의 프로필 이미지 URL |

