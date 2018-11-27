# 사용자 정의 스크립트 노드

챗봇의 데이터를 활용하여 프로그래밍 언어로 처리할 수 있는 사용자 정의 스크립트 노드를 사용할 수 있습니다.

## 실행환경

프로그래밍 언어: JavaScript<br/>
런타임: Node.js v8.10<br/>
타임아웃: 5,000ms<br/>
코드 길이: 10,000byte

만일 코드에서 오류가 발생하거나 수행시간이 5,000ms를 넘을 경우 스크립트는 종료되며,
챗봇은 최종 사용자에게 아무런 오류 메시지를 보내지 않습니다.

## 제공되는 Node.js 라이브러리

|패키지명|버전|
|:---|:---|
| apn | 2.2.0 |
| aws-sdk | 2.359.0 |
| bluebird | 3.5.3 |
| cheerio | 1.0.0-rc.2 |
| crypto | - |
| csv-parse | 4.0.1 |
| fetch | 1.1.0 |
| gm | 1.23.1 |
| googleapis | 35.0.0 |
| iconv-lite | 0.4.24 |
| imagemagick | 0.1.3 |
| lodash | 4.17.11 |
| moment | 2.22.2 |
| nodemailer | 4.7.0 |
| request | 2.88.0 |
| request-promise-native | 1.0.5 |
| superagent | 4.0.0 |
| underscore | 1.9.1 |
| uuid | 3.3.2 |
| xml2js | 0.4.19 |


## 핸들러 함수

사용자 정의 스크립트 노드의 code는 하나의 Node.js의 모듈 파일입니다.
챗봇은 `module.exports`에 핸들러에 선언된 스크립트를 실행합니다.
callback, Promise 두 가지 형태의 핸들러를 지원합니다.


### handler(context, callback): _void_

#### context <small>_(Object)_</small>
챗봇에서 전달 받는 객체

|Property|Type|Description|
|---|---|---|
|bot|[Bot](#type-bot)|챗봇의 정보|
|conversationId|String|진행 중인 대화의 UUID|
|endUserId|String|진행 중인 대화 고객의 UUID|
|params|Object|진행 중인 대화 파라미터 딕셔너리|
|platform|String|진행 중인 대화의 메시징 플랫폼 타입(`'kakao', 'kakaobiz', 'facebook', 'line', 'navertalk', 'bizchat', 'wechat', 'web', 'test'`)|
|userKey|String|메시징 플랫폼에서 제공하는 고객의 고유 Id|
|message|[Message](#type-message)|고객이 입력한 메시지|


#### callback(error, result) <small>_(Function)_</small>

챗봇에 결과를 전달하는 콜백 함수

|Argument|Type|Description
|---|---|---|
|error|Error|오류 발생시 전달할 객체|
|result|[HandlerResult](#type-handler-result)|스크립트 실행 결과로 전달할 객체

**Callback 예시**
```js
module.exports = function handler(context, callback) {
  callback(null, {
    message: {
      type: 'text',
      text: 'Hello CLOSER'
    }
  });
}
```


### handler(context): _Promise&lt;HandlerResult&gt;_
Promise형태로 결과값을 반환할 수 있습니다.

**Promise 예시**
```js
module.exports = function handler(context) {
  return new Promise((resolve, reject) => {
    resolve({
      message: {
        type: 'text',
        text: 'Hello CLOSER'
      }
    });
  });
}
```

**Async/Await 예시**
```js
module.exports = async function handler(context) {
  // const somePromise = ...
  // await somePromise;
  return {
    message: {
      type: 'text',
      text: 'Hello CLOSER'
    }
  };
}
```




### 데이터 타입

#### Bot <a id="type-bot"></a>
|Property|Type|Description|Required
|---|---|---|---|
|title|String|봇의 이름|Y
|description|String|봇의 설명|N

#### Message <a id="type-message"></a>
|Property|Type|Description|Required|
|---|---|---|---|
|type|String|메시지 타입 (`'text', 'media', 'cards', 'location'`)|Y
|text|String|메시지 텍스트|*
|media|Object|미디어|*
|button|Object|링크 버튼|N
|cards|Array&lt;Object&gt;|캐러셀 메시지|*
|location|Object|위치 메시지|*
\* `type`의 값에 해당하는 Property는 Required입니다.

#### HandlerResult <a id="type-handler-result"></a>
|Property|Type|Description| Required
|---|---|---|---|
|message|[Message](#type-message)|노드 실행 후 챗봇이 응답할 메시지|N
|custom|Object|이후 노드에서 `sandbox.result.custom`으로 접근할 객체|N
|params|Object|노드 실행 후 설정할 파라미터|N
