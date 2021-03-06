---
description: 대화 테스트 메뉴에서 제공되는 개발자 도구에 대해 알아봅시다.
---

# 개발자 도구

![&#xAC1C;&#xBC1C;&#xC790; &#xB3C4;&#xAD6C;](../../../.gitbook/assets/bot-inspector.gif)

개발자 도구는 대화 테스트 창 우측 상단에 위치한 버튼\(![](../../../.gitbook/assets/bot-inspector-icon.png)\) 을 눌러 활성화할 수 있습니다.   
활성화 시 노드의 실행 결과나 반환된 컨텍스트 등을 실시간으로 확인할 수 있는 등 작성한 시나리오를 분석하는 데 필요한 유용한 도구 모음들을 제공합니다. 더 자세한 사항은  아래 항목을 참고해주세요.

## 기능 소개

### 이전 위치로 돌아가기

![&#xC774;&#xC804; &#xC704;&#xCE58;&#xB85C; &#xB3CC;&#xC544;&#xAC00;&#xAE30; &#xB3D9;&#xC791; &#xC2DC;&#xC5F0;](../../../.gitbook/assets/bot-inspector-back.gif)

봇 메시지 위에 마우스 커서를 올려놓으면 돌아가기\(![](../../../.gitbook/assets/bot-inspector-back-icon.png)\) 버튼이 나타납니다.  
돌아가기 버튼을 누르면 해당 위치에서부터 시나리오를 다시 테스트하실 수 있습니다.

### 노드 추적 도구 \(Trace\)

![&#xB178;&#xB4DC; &#xBD84;&#xC11D; &#xB3C4;&#xAD6C; &#xD65C;&#xC6A9; &#xBAA8;&#xC2B5;](../../../.gitbook/assets/bot-inspector-node-example.png)

추적 도구에서는 답변 생성에 사용된 노드들을 확인할 수 있고, 각 노드의 [템플릿](../advanced/template-syntax.md) 결과 혹은 [컨텍스트](../advanced/context.md)의 변경도 함께 추적할 수 있습니다. \(위 예시는 파라미터 설정 노드의 템플릿 결과와 컨텍스트 변경사항을 보여줍니다.\)

노드 추적 도구에서 각 노드마다 표시되는 값들은 다음과 같습니다.

* 각 노드별 수행 시간 \(execution time\)
* 각 노드별 data 템플릿 적용 결과
* 각 노드별 context 변경점
* 노드에서 반환한 메시지 \(존재 시, 아이콘으로 표시\)

### 컨텍스트 분석 도구 \(Context\)

![&#xCEE8;&#xD14D;&#xC2A4;&#xD2B8; &#xBD84;&#xC11D; &#xB3C4;&#xAD6C; &#xD65C;&#xC6A9; &#xBAA8;&#xC2B5;](../../../.gitbook/assets/bot-inspector-context-pane.gif)

컨텍스트 분석 도구에서는 매 상호작용마다 반환되는 사용자의 컨텍스트 정보를 실시간으로 확인하고, 특정 반환값을 특정하여 조회할 수 있는 기능을 제공합니다. 주로 파라미터의 변화를 실시간으로 확인하거나, 다음 시나리오를 작성하기 전 이용할 값을 조회하고자 할 때 유용합니다.

컨텍스트 반환 값에 대해서는 다음 페이지를 참고해주세요.

{% page-ref page="../advanced/context.md" %}

{% hint style="warning" %}
컨텍스트 분석 도구에서는 **문서화되지 않은 값**들도 다수 존재합니다. 이는 시스템에서 사용되는 값으로, 별도로 명시되어 있지 않은 한 해당 값들을 추후 변경될 소지가 있으므로 이용을 권장하지 않습니다.

만일 문서화되지 않은 값들이 프로덕션에서 필요한 경우, 사용하기 전 support@closer.ai 로 먼저 문의해주세요.
{% endhint %}



