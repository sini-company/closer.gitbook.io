# HTTP 요청 노드

### **HTTP요청 노드\(HTTP Fetch Node\)**

* JSON / XML 형식의 데이터를 반환하는 외부 API와 연동할 때 사용할 수 있는 노드 입니다.
* GET, POST, DELETE, PUT 4 가지의 method를 지원하고, header와 body값을 설정할 수 있습니다.
* 반환값은 `fetch` context를 통해 획득할 수 있습니다.

#### fetch _\(object\)_

HTTP요청 노드 진행 후 생성되는 객체입니다.

| 파라미터 | 타입 | 설명 |
| :--- | :--- | :--- |
| uri | strng | 요청 URI |
| data | object | 서버에서 반환된 json / xml 데이터 |
| statusCode | number | 서버에서 반환한 statusCode \(200, 401 등\) |
| status | string | 성공시 'COMPLETED', 실패시 'FAILED' |
| error | Error | 요청 오류 |

* 응답 받은 데이터는 `{{fetch.data}}`와 같이 참조할 수 있으며, JSON타입인 경우 `{{fetch.data.path[2].your.object}}`와 같이 접근이 가능합니다.
* 아래는 네이버가 제공하는 파파고 영어번역API 연동 예시입니다.

![HTTP &#xC694;&#xCCAD; &#xB178;&#xB4DC; &#xC608;&#xC2DC;](../../../.gitbook/assets/builder_http_node.png)

### \*\*\*\* <a id="parameter-node"></a>

