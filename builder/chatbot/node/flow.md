---
description: 챗봇이 진행중인 플로우에서 다른 플로우로 이동하도록 시나리오 흐름을 변경하는 노드
---

# 플로우 연결 노드

![&#xD50C;&#xB85C;&#xC6B0; &#xC5F0;&#xACB0; &#xB178;&#xB4DC;](../../../.gitbook/assets/guide_%20%2816%29.png)

플로우를 기능 또는 시나리오 단위로 잘 분리해 놓은 경우, 플로우 연결 노드를 통해 다른 플로우에서 특정 플로우로 이동하도록 챗봇 시나리오를 설계할 수 있습니다.

만일 챗봇 플로우 상에서 마지막 노드에 연결된 플로우나 노드 없이 시나리오가 끝나게 된다면 챗봇은 폴백 플로우로 이동하게 됩니다. 이에 대해서는 [시스템 플로우](../flow.md#undefined) 항목을 참고해주세요. 

## 고급 기능

![&#xD50C;&#xB85C;&#xC6B0; &#xC5F0;&#xACB0; &#xB178;&#xB4DC; - &#xACE0;&#xAE09; &#xC124;&#xC815;](../../../.gitbook/assets/image%20%2852%29.png)

![](../../../.gitbook/assets/node-form-advanced-checkbox.png)를 활성화한 경우 flowId 외에도 nodeId를 설정할 수 있게 되는데, 이를 이용하면 해당 플로우의 진입 노드가 아닌 특정 노드로 이동시킬 수 있습니다. \(nodeId는 캔버스 상의 노드 오른쪽 상단의 숫자를 통해 확인할 수 있습니다.\)

flow 입력 공간에도 지정된 드롭다운 목록 외에 위 스크린샷과 같이 템플릿 문법을 이용하여 flowId를 직접 지정할 수 있습니다. \(flowId는 현재 봇 빌더의 URL주소를 통해 확인할 수 있습니다.\) 이를 통해 [파라미터](parameter.md)나 [포스트백 페이로드](../advanced/postback-payload.md#1-flow-navigation)를 통해 flowId를 동적으로 설정할 수 있습니다.

