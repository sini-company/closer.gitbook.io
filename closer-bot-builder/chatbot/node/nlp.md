# 자연어 처리 노드 👩🏻‍🔬

### **자연어 처리 노드**   <a id="nlp-node"></a>

![&#xC790;&#xC5F0;&#xC5B4; &#xCC98;&#xB9AC; &#xB178;&#xB4DC;](../../../.gitbook/assets/guide_%20%2811%29.png)

자연어처리 노드는 **사용자가 입력한 메시지**\(`messsage.text`값\) 를 **외부 자연어처리 에이전트를 통해 분석**하고 그 결과를 반환해주는 노드입니다. 따라서 [텍스트 입력 요청 노드 ](request.md#text)이후에 자연어 처리 노드를 배치하여 주셔야 올바른 결과를 획득하실 수 있습니다.

분석할 의도\(intent\)나 개체\(entity\) 등은 외부 자연어처리 에이전트를 통해 설정하셔야 하며, 현재 DialogFlow와 Watson Conversation 두 가지 에이전트를 지원합니다. 각 에이전트의 사용방법은 공식 홈페이지를 참고해 주세요.

* [https://dialogflow.com/docs/tutorial-build-an-agent](https://dialogflow.com/docs/tutorial-build-an-agent) 
* [https://www.ibm.com/watson/kr-ko/developercloud/conversation.html](https://www.ibm.com/watson/kr-ko/developercloud/conversation.html)

{% hint style="info" %}
자연어 처리 에이전트 관리는 **내 프로필 &gt; 자연어 처리 API 관리** 메뉴를 통해 이용할 수 있습니다.  
[https://app.closer.ai/app/settings/nlp](https://app.closer.ai/app/settings/nlp) 
{% endhint %}

분석된 결과는 컨텍스트 객체의 `nlp` 값에 반환됩니다. 여기서 이용할 수 있는 속성은 다음과 같습니다. 

| 경로 | 자료형 | 설명 |
| :--- | :--- | :--- |
| nlp.intent | string | 분석된 의도 |
| nlp.entities | \[{entity: string, value: string, score: number}\] | 분석된 개체 |
| nlp.answer | string | 생성된 답변 \(제공 시\) |
| nlp.score | number | 분석 정확도 \(제공 시\) |
| nlp.error | Error | 요청 오류 / 분석 오류 \(실패 시\) |



