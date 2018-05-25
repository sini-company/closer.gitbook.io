## WebChat SDK 버전 {#CLOSERWebChatSDK연동가이드v0.1-WebChatSDK버전}

* 0.22.8

## WebChat SDK 초기화 {#CLOSERWebChatSDK연동가이드v0.1-WebChatSDK초기화}

* apiKey : 필수, CLOSER에서 제공하는 API 접근 키

```
var webchatSDK = new CloserSDK.WebChat({
  apiKey: '{closer-api-token}'
});
```

## WebChatClient 생성 {#CLOSERWebChatSDK연동가이드v0.1-WebChatClient생성}

* userKey : 선택, 기본값으로 browser fingerprint 사용, 최종사용자의 고유 ID로 String 타입
* botId : 필수, CLOSER에서 생성한 Bot의 ID
* params : 선택, 초기 파라미터 주입

```
var wsClient = webchatSDK.open({
  userKey: '{closer-enduser-key}',
  botId: '{botId}',
  params: {}
});
```

## Open / Close / Message Listener 추가 / 제거 {#CLOSERWebChatSDK연동가이드v0.1-Open/Close/MessageListener추가/제거}

```
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

## 메시지 전송 \(high-level\) {#CLOSERWebChatSDK연동가이드v0.1-메시지전송(high-level)}

```
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

## 메시지 전송 \(low-level\) {#CLOSERWebChatSDK연동가이드v0.1-메시지전송(low-level)}

```
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

### Objects {#CLOSERWebChatSDK연동가이드v0.1-Objects}

### MESSAGE {#CLOSERWebChatSDK연동가이드v0.1-MESSAGE}

CLOSER 메시지 Object로 메시지 송/수신에 사용됩니다.

메시지 전송시에는 text / media / location 전송만 지원합니다.

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | STRING | N | 메시지의 ID. CLOSER에서 자동으로 생성됨 |
| endUserId | UUID | N | 최종사용자의 ID. CLOSER에서 자동으로 생성됨 |
| conversationId | UUID | N | 대화의 ID. CLOSER에서 자동으로 생성됨 |
| data | Object\(MESSAGE.DATA\) | Y | 메시지의 데이터. MESSAGE.DATA 참고 |
| meta | Object\(MESSAGE.META\) | N | 메시지의  메타데이터. MESSAGE.META 참고 |
| isUser | BOOLEAN | N | 최종사용자인 경우 true, 그 외에는 false |
| timestamp | UNIX Timestamp with milliseconds | N | 메시지 발행 시간 |

#### MESSAGE.DATA {#CLOSERWebChatSDK연동가이드v0.1-MESSAGE.DATA}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| type | 'text', 'media', 'cards', 'location' | Y | 메시지의 타입. text : 텍스트 메시지, media : 이미지, 동영상, 오디오 등의 미디어, cards : 카드 타입 리스트 \(Carousel로 사용\), location: 위치 정보 \(latitude, longitude\) |
| text | STRING | C | text 타입인 경우 필수 |
| media | Object\(MESSAGE.DATA.MEDIA\) | C | media 타입인 경우 필수 |
| cards | Array\(Object\(MESSAGE.DATA.CARD\)\) | C | cards 타입인 경우 필수 |
| location | Object\(MESSAGE.DATA.LOCATION\) | C | location 타입인 경우 필수 |
| button | Object\(MESSAGE.DATA.BUTTON\) | N | 메시지에 포함된 버튼으로 KEYBOARD.BUTTON과는 형식과 동작이 다름 링크 삽입 가능 |

#### MESSAGE.META {#CLOSERWebChatSDK연동가이드v0.1-MESSAGE.META}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| sender | Object\(MESSAGE.META.SENDER\) | N | 메시지를 전송한 전송자의 정보 |

#### MESSAGE.DATA.MEDIA {#CLOSERWebChatSDK연동가이드v0.1-MESSAGE.DATA.MEDIA}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| contentType | 'image', 'video', 'audio', 'link' | Y | 이미지, 동영상, 오디오, 링크 |
| uri | STRING | Y | 이미지, 동영상, 오디오, 링크의 URL |

#### MESSAGE.DATA.BUTTON {#CLOSERWebChatSDK연동가이드v0.1-MESSAGE.DATA.BUTTON}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| label | STRING | Y | 버튼 인터페이스에 노출할 이름 |
| uri | STRING | N | 버튼이 링크로 동작 시 URL, 없으면 키보드 입력 동작 |

#### MESSAGE.DATA.CARD {#CLOSERWebChatSDK연동가이드v0.1-MESSAGE.DATA.CARD}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| title | STRING | Y | 카드의 제목 |
| description | STRING | N | 카드의 설명 |
| media | Object\(MESSAGE.DATA.MEDIA\) | N | 카드에 포함될 미디어 |
| uri | STRING | N | 카드 선택시 이동할 링크 URL |
| buttons | Array\(Object\(MESSAGE.DATA.BUTTON\)\) | N | 카드에 포함된 버튼 리스트 |

#### MESSAGE.DATA.LOCATION {#CLOSERWebChatSDK연동가이드v0.1-MESSAGE.DATA.LOCATION}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| title | STRING | N | 위치의 이름 |
| latitude | NUMBER | Y | GPS Latitude |
| longitude | NUMBER | Y | GPS longitude |

#### MESSAGE.META.SENDER {#CLOSERWebChatSDK연동가이드v0.1-MESSAGE.META.SENDER}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| userKey | STRING | Y | SENDER 사용 시 필수. 전송자의 ID |
| platform | STRING | Y | SENDER 사용 시 필수. 전송자의 플랫폼 |

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
| min | NUMBER | C | number 타입인 경우에 필수, 최소값 |
| max | NUMBER | C | number 타입인 경우에 필수, 최대값 |
| parse | BOOLEAN | N | false인 경우 숫자만 입력 가능, true인 경우 주어진 문자열에서 숫자만 읽어들임 |
| integer | BOOLEAN | N | false인 경우 Integer만 입력 가능 |
| buttons | Array\(Object\(KEYBOARD.BUTTON\)\) | C | buttons 타입인 경우에 필수 |

#### KEYBOARD.BUTTON {#CLOSERWebChatSDK연동가이드v0.1-KEYBOARD.BUTTON}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| label | STRING | Y | 버튼 인터페이스에 노출할 이름 |
| params | Object\(DICTIONARY\) | N | 버튼 선택 시 저장되는 파라미터. key - value dictionary 타입 |

## CONTEXT {#CLOSERWebChatSDK연동가이드v0.1-CONTEXT}

CLOSER에서 대화를 진행하는데 필요한 정보입니다. SDK의 WebChatClient가 Open되면 Context를 message listener에 전송합니다.

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| botId | STRING | Y | Bot의 ID |
| conversationId | UUID | Y | 대화의 ID. CLOSER에서 자동으로 생성됨 |
| endUserId | UUID | Y | 최종사용자의 ID. CLOSER에서 자동으로 생성됨 |
| navigation | Object\(CONTEXT.NAVIGATION\) | N | 현재 대화의 위치를 표현하는 오브젝트 |
| params | Object\(DICTIONARY\) | N | 현재 대화에서 사용하고 있는 파라미터 |
| platform | 'web' | Y | 현재 대화의 플랫폼, WebChatSDK에서는 'web'만 사용 |
| userKey | STRING | Y | 최종사용자 식별 키. SDK Open시 주입한 값 |

### CONTEXT.NAVIGATION {#CLOSERWebChatSDK연동가이드v0.1-CONTEXT.NAVIGATION}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| lastNode | Object\(CONTEXT.NAVIGATION.LASTNODE\) | Y | 마지막 노드의 정보 |
| prevFlow | NUMBER | N | 이전 플로우의 ID |

### CONTEXT.NAVIGATION.LASTNODE {#CLOSERWebChatSDK연동가이드v0.1-CONTEXT.NAVIGATION.LASTNODE}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| flowId | NUMBER | Y | 현재 노드의 플로우 ID |
| nodeId | NUMBER | Y | 현재 노드의 ID |
| visitCount | NUMBER | N | 최종사용자가 노드에 방문한 수 |

## AGENT {#CLOSERWebChatSDK연동가이드v0.1-AGENT}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| id | STRING | Y | 상담원의 User ID |
| profile | Object\(AGENT.PROFILE\) | N | 상담원의 profile 정보 |

### AGENT.PROFILE {#CLOSERWebChatSDK연동가이드v0.1-AGENT.PROFILE}

| 키 | 타입 | 필수 | 설명 |
| :--- | :--- | :--- | :--- |
| displayName | STRING | N | 상담원의 DisplayName |
| picture | URL | N | 상담원의 프로필 이미지 URL |



