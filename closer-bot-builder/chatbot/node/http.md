---
description: 공개 HTTP API와 그 반환값을 이용할 수 있는 노드
---

# HTTP 요청 노드

### **HTTP요청 노드\(HTTP Fetch Node\)**

HTTP 요청 노드는 공개된 HTTP API를 이용하여 해당 반환값을 CLOSER 챗봇 시나리오에 활용할 수 있게끔 도와주는 역할을 합니다.

* GET, POST, PUT, DELETE 네 가지 method를 이용할 수 있습니다.
* HTTP 요청 결과는 `fetch` context 를 통해 획득할 수 있습니다. \(text / json 형식의 데이터를 지원합니다.\)

#### fetch _\(object\)_

HTTP 요청 수행 후 생성되는 반환값을 담고 있는 객체입니다.

| 파라미터 | 타입 | 설명 |
| :--- | :--- | :--- |
| uri | strng | 요청 URI |
| data | object | 서버에서 반환된 데이터 \(json / text 형식\) |
| statusCode | number | 서버에서 반환한 statusCode \(200, 401 등\) |
| status | string | 성공시 'COMPLETED', 실패시 'FAILED' |
| error | Error | 요청 오류 |

* 응답 받은 데이터는 `{{fetch.data}}`경로로 접근할 수 있으며, 반환값이 JSON 형태인 경우 `{{fetch.data.path[2].your.object}}`와 같이 접근이 가능합니다.

다음은 네이버가 제공하는 파파고 영어번역 API 연동 설정 예시입니다.   
실제 API와는 다를 수 있으니 참고용으로만 확인해 주세요.  


![HTTP &#xC694;&#xCCAD; &#xB178;&#xB4DC; &#xC124;&#xC815; &#xC608;&#xC2DC; \(&#xCC38;&#xACE0;&#xC6A9;\)](../../../.gitbook/assets/http-example.png)

