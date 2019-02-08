---
description: CLOSER 챗봇이 고객과 대화하는 맥락을 보관하는 객체인 컨텍스트에 대하여 알아봅니다.
---

# 컨텍스트 \(Context\)

CLOSER 챗봇에서는 사용자의 마지막 입력이나 다른 노드의 수행 결과값들이 담겨있는 컨텍스트\(Context\)라는 객체를 제공합니다. 여기에는 다음과 같은 값들이 제공됩니다.

{% hint style="info" %}
아직 Context 대한 문서는 100% 완성되지 않았습니다.   
각 노드별 반환값에 대한 설명은 추후 추가될 예정입니다.
{% endhint %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">키 (key)</th>
      <th style="text-align:left">값 (value)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">botId</td>
      <td style="text-align:left">CLOSER에서 제공하는 챗봇의 고유 식별자</td>
    </tr>
    <tr>
      <td style="text-align:left">endUserId</td>
      <td style="text-align:left">CLOSER에서 제공하는 고객의 고유 식별자
        <br />(⚠️ 대화 테스트에는 존재하지 않습니다.)</td>
    </tr>
    <tr>
      <td style="text-align:left">conversationId</td>
      <td style="text-align:left">
        <p>CLOSER에서 제공하는 고객의 대화 세션의 고유 식별자</p>
        <p>(⚠️ 대화 세션이 변경되면 함께 변경됩니다. e.g. 친구 삭제 후 다시 추가 시)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">platform</td>
      <td style="text-align:left">고객의 유입 채널 (e.g. <code>facebook</code>, <code>kakao</code>, <code>web</code>,
        ...)</td>
    </tr>
    <tr>
      <td style="text-align:left">userKey</td>
      <td style="text-align:left">고객의 유입 채널에서 제공되는 고유 식별자</td>
    </tr>
    <tr>
      <td style="text-align:left">message</td>
      <td style="text-align:left">
        <p>고객으로부터 입력받은 마지막 메시지 데이터</p>
        <ul>
          <li>type: <code>text</code> / <code>media</code> / ...</li>
          <li>text: 텍스트 메시지의 경우의 메시지 값</li>
          <li>payload: 고객이 postback 버튼을 선택했을 경우의한 <a href="../node/response.md#postback-payload">포스트백 데이터</a> (존재
            시)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">params</td>
      <td style="text-align:left">챗봇에 설정된 파라미터 객체</td>
    </tr>
    <tr>
      <td style="text-align:left">error</td>
      <td style="text-align:left">답변 생성 과정에서 발생한 오류 (예: 메시지 없음, 연결된 플로우 없음 등)</td>
    </tr>
    <tr>
      <td style="text-align:left">[NODE_TYPE]</td>
      <td style="text-align:left">
        <p>노드의 실행 결과가 담겨있는 객체</p>
        <ul>
          <li>status: 노드의 실행 상태 (e.g. <code>PENDING</code>, <code>COMPLETED</code>, <code>FAILED</code>)</li>
          <li>error: 노드의 실행 오류 (예: 템플릿 문법 오류나 잘못된 데이터 등의 오류 발생 시)</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>{% hint style="warning" %}
endUserId와 userKey 둘 다 고객을 특정하는 고유 식별자로 사용할 수 있습니다.   
다만 userKey의 경우는 유입 채널에서 설정되는 값이기 때문에 채널을 여러 가지 설정하신 경우에 충돌이 발생할 수 있으니 platform값과 같이 사용하셔야 됩니다.
{% endhint %}

컨텍스트에 존재하는 값들은 템플릿 문법을 이용하여 어디에서든 참조하여 답변 생성에 활용할 수 있습니다. 더 자세한 내용은 템플릿 문법 사용법을 통해 알아보세요.

{% page-ref page="template-syntax.md" %}

