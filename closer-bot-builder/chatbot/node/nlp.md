# 자연어 처리 노드 👩🏻‍🔬

### **자연어 처리 노드**   <a id="nlp-node"></a>

![&#xC790;&#xC5F0;&#xC5B4; &#xCC98;&#xB9AC; &#xB178;&#xB4DC; &#xC608;&#xC2DC;](../../../.gitbook/assets/guide_%20%2811%29.png)

* 사용자의 자연어 입력을 분석하고 그 결과를 이용하고자 할때 사용하는 노드입니다. 
* 자연어 처리를 위해서는 외부 자연어 에이전트를 설정하여야 합니다.
  * 현재 DialogFlow, Watson Conversation 두 가지 에이전트를 지원합니다.
* 분석 결과는 `nlp` 컨텍스트에 저장되어 반환됩니다.

| 경로 | 자료형 | 설 |
| :--- | :--- | :--- |
| nlp.intent | string | 분석된 의도 |
| nlp.entities | \[{entity: string, value: string, score: number}\] | 분석된 개체 |
| nlp.answer | string | 생성된 답변 \(제공 시\) |
| nlp.score | number | 분석 정확도 \(제공 시\) |

