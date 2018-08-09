# CLOSER Webhook 연동 가이드

CLOSER에서는 Webhook으로 봇/사용자/상담원의 메시지와 이벤트를 전달합니다.

본 문서에서는 CLOSER에서 전송하는 Webhook을 연동할 수 있도록, Webhook의 포맷과 설정 방법등을 명세합니다.

## Webhook 설정 단계

1. 본 문서에서 명세하는 Webhook의 포맷에 따라, 목적에 맞는 API를 개발하세요.
2. CLOSER Bot에서 개발하신 API의 URL을 등록합니다.
3. CLOSER의 Bot을 사용시 발생하는 이벤트를 개발하신 API로 전송합니다.

## CLOSER에서 전송하는 Webhook 본문 포맷

### Webhook Payload Example

```text
{
    "type": "message_sent",
    "botId": "Bp2gkd",
    "message": {
        "timestamp": "2018-02-05T03:50:54.887Z",
        "data": {
            "text": "안녕하세요. 시작 메시지 입니다.",
            "type": "text"
        },
        "id": "bb2b8e8c-7b32-47a4-a1b1-3c15ce530a80",
        "conversationId": "b2df2960-62f4-408a-86d4-d484dea51d74",
        "isUser": false
    },
    "timestamp": "2018-02-05T03:50:54.888Z",
    "endUserId": "0369b88b-168e-4946-9d29-df5b456b6a30",
    "conversation": {
        "id": "b2df2960-62f4-408a-86d4-d484dea51d74",
        "params": {},
        "navigation": {
            "lastNode": {
                "flowId": 1,
                "nodeId": 3,
                "visitCount": 1
            }
        },
        "platform": "web",
        "userKey": "978bd68d3954cf4ac21e1d0f4918ab0a"
    }
}
```

### type \(string\)

* 'message\_received' : 받은 메시지
* 'message\_sent' : 보낸 메시지
* 'friend\_removed' : 친구 삭제 \(메신저별로 다를 수 있음\)
* 'friend\_added' : 친구 추가
* 'session\_started' : 세션 시작
* 'session\_expired' : 세션 종료
* 'agent\_call\_requested' : 상담 요청
* 'agent\_call\_connected' : 상담 시작
* 'agent\_call\_disconnected : 상담 종료

### **platform \(string\)**

* 'facebook', 'kakao', 'kakaobiz', 'line', 'navertalk', 'web', 'wechat'

### **userKey \(string\)**

* 사용자 식별 키

### **botId \(string\)**

* CLOSER의 봇 ID

### **conversation \(JSON Object\)**

* CLOSER의 Conversation 데이터
* **id \(UUID\)**

   : Conversation ID

* **params \(JSON Object\)**

   : CLOSER Bot에서 설정한 파라미터 중 봇 사용자가 선택한 파라미터 키와 값

### **timestamp \(DateTime\)**

* wehook event 전송 시간

### **message \(JSON Object\)**

* CLOSER의 Message 데이터
* **timestamp \(DateTime\)**

   : 메시지 전송 시간

* **data \(JSON Object\)**

   : text / media / button / cards

* **meta \(JSON Object\)**

   : message의 메타데이터

* **id \(UUID\)**

   : CLOSER의 Message ID

* **isUser \(boolean\)**

   : true인 경우 End User \(메신저 사용자\), false인 경우 봇 or 상담원

## Webhook 설정

* CLOSER Bot &gt;  봇 정보 설정 &gt;  Webhook 설정 에서 Webhook을 받을 주소를 설정할 수 있습니다.

![](https://closer.atlassian.net/wiki/download/attachments/39452673/스크린샷%202018-02-05%20오후%2012.46.29.png?version=1&modificationDate=1517803922097&cacheVersion=1&api=v2)

