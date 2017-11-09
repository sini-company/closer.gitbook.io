# 파라미터 (Parameters)

대화에서 발생한 값들을 key-value 형식으로 유지할때 사용합니다.

시스템에서 기본적으로 제공하는 예약 파라미터를 제외하고, 사용자는 파라미터 노드에서 원하는 값을 설정하여 [템플릿 문법](/chapter1/c790-c720-b86d-ac8c-bd07-c124-acc4-d558-ae3028-flow-editor/b178-b4dc/d15c-d50c-b9bf-bb38-bc95-template-syntax.md)을 이용해 다음 노드의 입력값으로 사용할 수 있습니다.

## 예약 파라미터 (Reserved Parameters) {#reserved-parameters}

| 파라미터 명 | 설명 |
| :--- | :--- |
| `id` | 사용자의 대화 (Conversation) 를 식별하는 키 |
| `platform` | 사용자가 유입된 메신저 플랫폼을 나타내는 키<br>`web`, `kakao`, `kakaobiz`, `facebook`, `line`, `navertalk`, `wechat` |
| `userKey` | 각 메신저 플랫폼에서 설정된 사용자 식별 키 |
| `message` | 사용자가 마지막으로 입력한 텍스트 메시지 |
