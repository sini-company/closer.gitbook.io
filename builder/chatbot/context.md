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
      <th style="text-align:left">&#xD0A4; (key)</th>
      <th style="text-align:left">&#xAC12; (value)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">botId</td>
      <td style="text-align:left">CLOSER&#xC5D0;&#xC11C; &#xC81C;&#xACF5;&#xD558;&#xB294; &#xCC57;&#xBD07;&#xC758;
        &#xACE0;&#xC720; &#xC2DD;&#xBCC4;&#xC790;</td>
    </tr>
    <tr>
      <td style="text-align:left">endUserId</td>
      <td style="text-align:left">CLOSER&#xC5D0;&#xC11C; &#xC81C;&#xACF5;&#xD558;&#xB294; &#xACE0;&#xAC1D;&#xC758;
        &#xACE0;&#xC720; &#xC2DD;&#xBCC4;&#xC790;
        <br />(&#x26A0;&#xFE0F; &#xB300;&#xD654; &#xD14C;&#xC2A4;&#xD2B8;&#xC5D0;&#xB294;
        &#xC874;&#xC7AC;&#xD558;&#xC9C0; &#xC54A;&#xC2B5;&#xB2C8;&#xB2E4;.)</td>
    </tr>
    <tr>
      <td style="text-align:left">conversationId</td>
      <td style="text-align:left">
        <p>CLOSER&#xC5D0;&#xC11C; &#xC81C;&#xACF5;&#xD558;&#xB294; &#xACE0;&#xAC1D;&#xC758;
          &#xB300;&#xD654; &#xC138;&#xC158;&#xC758; &#xACE0;&#xC720; &#xC2DD;&#xBCC4;&#xC790;</p>
        <p>(&#x26A0;&#xFE0F; &#xB300;&#xD654; &#xC138;&#xC158;&#xC774; &#xBCC0;&#xACBD;&#xB418;&#xBA74;
          &#xD568;&#xAED8; &#xBCC0;&#xACBD;&#xB429;&#xB2C8;&#xB2E4;. e.g. &#xCE5C;&#xAD6C;
          &#xC0AD;&#xC81C; &#xD6C4; &#xB2E4;&#xC2DC; &#xCD94;&#xAC00; &#xC2DC;)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">platform</td>
      <td style="text-align:left">&#xACE0;&#xAC1D;&#xC758; &#xC720;&#xC785; &#xCC44;&#xB110; (e.g. <code>facebook</code>, <code>kakao</code>, <code>web</code>,
        ...)</td>
    </tr>
    <tr>
      <td style="text-align:left">userKey</td>
      <td style="text-align:left">&#xACE0;&#xAC1D;&#xC758; &#xC720;&#xC785; &#xCC44;&#xB110;&#xC5D0;&#xC11C;
        &#xC81C;&#xACF5;&#xB418;&#xB294; &#xACE0;&#xC720; &#xC2DD;&#xBCC4;&#xC790;</td>
    </tr>
    <tr>
      <td style="text-align:left">message</td>
      <td style="text-align:left">
        <p>&#xACE0;&#xAC1D;&#xC73C;&#xB85C;&#xBD80;&#xD130; &#xC785;&#xB825;&#xBC1B;&#xC740;
          &#xB9C8;&#xC9C0;&#xB9C9; &#xBA54;&#xC2DC;&#xC9C0; &#xB370;&#xC774;&#xD130;</p>
        <ul>
          <li>type: <code>text</code> / <code>media</code> / ...</li>
          <li>text: &#xD14D;&#xC2A4;&#xD2B8; &#xBA54;&#xC2DC;&#xC9C0;&#xC758; &#xACBD;&#xC6B0;&#xC758;
            &#xBA54;&#xC2DC;&#xC9C0; &#xAC12;</li>
          <li>payload: &#xACE0;&#xAC1D;&#xC774; postback &#xBC84;&#xD2BC;&#xC744; &#xC120;&#xD0DD;&#xD588;&#xC744;
            &#xACBD;&#xC6B0;&#xC758; <a href="node/response.md#postback-payload">&#xD3EC;&#xC2A4;&#xD2B8;&#xBC31; &#xB370;&#xC774;&#xD130;</a> (&#xC874;&#xC7AC;
            &#xC2DC;)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">params</td>
      <td style="text-align:left">&#xCC57;&#xBD07;&#xC5D0; &#xC124;&#xC815;&#xB41C; &#xD30C;&#xB77C;&#xBBF8;&#xD130;
        &#xAC1D;&#xCCB4;</td>
    </tr>
    <tr>
      <td style="text-align:left">error</td>
      <td style="text-align:left">&#xB2F5;&#xBCC0; &#xC0DD;&#xC131; &#xACFC;&#xC815;&#xC5D0;&#xC11C; &#xBC1C;&#xC0DD;&#xD55C;
        &#xC624;&#xB958; (&#xC608;: &#xBA54;&#xC2DC;&#xC9C0; &#xC5C6;&#xC74C;,
        &#xC5F0;&#xACB0;&#xB41C; &#xD50C;&#xB85C;&#xC6B0; &#xC5C6;&#xC74C; &#xB4F1;)</td>
    </tr>
    <tr>
      <td style="text-align:left">[NODE_TYPE]</td>
      <td style="text-align:left">
        <p>&#xB178;&#xB4DC;&#xC758; &#xC2E4;&#xD589; &#xACB0;&#xACFC;&#xAC00; &#xB2F4;&#xACA8;&#xC788;&#xB294;
          &#xAC1D;&#xCCB4;</p>
        <ul>
          <li>status: &#xB178;&#xB4DC;&#xC758; &#xC2E4;&#xD589; &#xC0C1;&#xD0DC; (e.g. <code>PENDING</code>, <code>COMPLETED</code>, <code>FAILED</code>)</li>
          <li>error: &#xB178;&#xB4DC;&#xC758; &#xC2E4;&#xD589; &#xC624;&#xB958; (&#xC608;:
            &#xD15C;&#xD50C;&#xB9BF; &#xBB38;&#xBC95; &#xC624;&#xB958;&#xB098; &#xC798;&#xBABB;&#xB41C;
            &#xB370;&#xC774;&#xD130; &#xB4F1;&#xC758; &#xC624;&#xB958; &#xBC1C;&#xC0DD;
            &#xC2DC;)</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

{% hint style="warning" %}
endUserId와 userKey 둘 다 고객을 특정하는 고유 식별자로 사용할 수 있습니다.   
단, userKey는 **메시징 채널에서 제공하는 값**으로 메시징 채널을 여러개 연동 시 값이 중복될 수 있습니다. 
{% endhint %}

실제 컨텍스트에 존재하는 값들을 더 자세히 확인해보시려면 개발자 도구 항목의 **컨텍스트 분석 도구** 항목을 확인해보세요.

{% page-ref page="advanced/inspector.md" %}

컨텍스트에 존재하는 값들은 템플릿 문법을 이용하여 답변 생성에 사용할 수 있습니다. 더 자세한 내용은 템플릿 문법 사용법을 통해 알아보세요.

{% page-ref page="advanced/template-syntax/" %}

