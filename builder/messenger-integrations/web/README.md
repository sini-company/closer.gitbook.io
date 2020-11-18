---
description: '홈페이지에 챗봇과 대화하는 버튼을 삽입하거나, 챗봇과 대화 가능한 링크를 생성하는 방법을 확인하세요.'
---

# 웹사이트 연동

![CLOSER &#xCC44;&#xD305; &#xC5F0;&#xB3D9; &#xC608;&#xC2DC;](../../../.gitbook/assets/image%20%2835%29.png)

CLOSER에서는 웹사이트에 실시간 채팅을 연동할 수 있도록 다음 두 가지 연동 방식을 제공합니다.

### **1. 원하는 웹 페이지에 설치 스크립트 `<script />` 삽입**

* 원하는 웹 페이지\(html\)에 CLOSER에서 제공하는 `<script />` 를 추가하는 것으로 쉽게 설치가 가능합니다.
* 페이지별로 기존에 설정한 테마나 파라미터 등을 커스터마이징하는 기능도 제공됩니다. \([고급 설정](./#advanced) 참고\) 

### **2. CLOSER 채팅창 링크 이용** 

* CLOSER 대화창이 표시되는 URL을 직접 이용합니다.
* 문자 메세지 등을 통한 아웃바운드 마케팅 링크에 사용하거나, 직접 iframe 등을 통해 웹 채팅을 관리할 수 있습니다.

{% hint style="info" %}
구버전 웹사이트 연동 도움말은 [웹사이트 연동 \(v1\)](v1.md) 페이지를 참고해주세요. 
{% endhint %}

## 설정 방법 <a id="configuration"></a>

1. 연동하고자 하는 챗봇의 **메신저 연동** 메뉴로 진입합니다.
2. 메신저 연동 페이지에서 **웹챗** 항목의 **설정** 버튼을 클릭합니다.
3. **웹챗 활성화** 스위치를 통해 언제든 즉시 활성화 / 비활성화가 가능합니다.

![&#xBD07; &#xAD00;&#xB9AC; &#xD398;&#xC774;&#xC9C0; &amp;gt; Settings &amp;gt; &#xBA54;&#xC2E0;&#xC800; &#xC5F0;&#xB3D9;](../../../.gitbook/assets/image%20%2824%29.png)

![&#xC6F9;&#xC0AC;&#xC774;&#xD2B8; &#xC5F0;&#xB3D9; &#xC124;&#xC815; &#xD654;&#xBA74; \(&#xC608;&#xC2DC;\)](../../../.gitbook/assets/image%20%2863%29.png)

## 테마 설정 <a id="theme"></a>

![&#xCC44;&#xD305;&#xCC3D; &#xD14C;&#xB9C8; &#xC124;&#xC815; &#xD654;&#xBA74; \(&#xC608;&#xC2DC;\)](../../../.gitbook/assets/image%20%2864%29.png)

CLOSER가 제공하는 웹 채팅 위젯은 현재 색상이나 버튼 등의 간단한 커스터마이징을 지원하고 있습니다.  
커스터마이징 지원은 추후 계속 확대될 예정입니다.

## 고급 설정 <a id="advanced"></a>

### Embedded WebChat API \(설치형 스크립트 API\) <a id="webchat-script-api"></a>

`<script />` 설치 방식을 이용할 경우, 웹페이지에 설치된 WebChat controller를 제어할 수 있는 API를 제공합니다. 초기 사용자 파라미터를 설정하거나, 노출 위치 변경 등이 필요한 경우 사용해보세요.  

#### API 이용 예시

{% tabs %}
{% tab title="변수 바인딩 예시" %}
```markup
<script>
  /* CLOSER에서 제공된 설치 스크립트 (botId를 변경 후 사용해주세요.) */
  (function (c, l, o, s, e, r) {
  c[e] = c[e] || {}; r = l.createElement('script'); s && (o += '?botId=' + s); e && (o += ('&bind=' + e)); r.src = o; r.async = 1; l.head.appendChild(r);
  })(window, document, 'https://app.closer.ai/webchat.js', '[botId]', 'webchat')
  
  // userKey를 변경합니다.
  // webchat.setUserKey('userKey');
  
  // 파라미터를 수정합니다.
  // webchat.setParams({ email: "user@email.com" });
  
  // webchat을 활성화/비활성화합니다.
  // webchat.setEnable(true);
  // webchat.setEnable(false);

  // webchat 대화창을 열고 닫습니다.
  // webchat.setOpen(true);
  // webchat.setOpen(false);
</script>
```
{% endtab %}

{% tab title="init 함수 예시" %}
```typescript
<script>
  /* CLOSER webchat 시작 파라미터 사용자화 + control 객체 획득 */
  var onLoadCallbackName = '$$_onload';
  window[onLoadCallbackName] = function (init) {
    delete window[onLoadCallbackName];
    
    // webchat을 설치합니다.
    var webchat = init({
      // 기본 theme를 변경합니다.
      theme: { 
        position:'right', 
        pageMargin: [26,30], // 좌우 margin, 상하 margin
        zIndex: 10000 // zIndex가 기존 UI와 겹칠 경우 이용하세요.
      } 
    });
    
    // userKey를 변경합니다.
    // webchat.setUserKey('userKey');
    
    // 파라미터를 수정합니다.
    // webchat.setParams({ email: "user@email.com" });
    
    // webchat을 활성화/비활성화합니다.
    // webchat.setEnable(true);
    // webchat.setEnable(false);

    // webchat 대화창을 열고 닫습니다.
    // webchat.setOpen(true);
    // webchat.setOpen(false);
  }

  /* CLOSER에서 제공된 설치 스크립트 (botId를 변경 후 사용해주세요.) */
  (function (c, l, o, s, e, r) {
  c[e] = c[e] || {}; r = l.createElement('script'); s && (o += '?botId=' + s); e && (o += ('&bind=' + e)); r.src = o; r.async = 1; l.head.appendChild(r);
  })(window, document, 'https://app.closer.ai/webchat.js', '[botId]', onLoadCallbackName)
</script>
```
{% endtab %}
{% endtabs %}

기본 제공 설치 스크립트의 호출 부분에는  `[botId]` 다음의 5번째 인자 부분이 비어있습니다.  여기에 CLOSER Webchat 스크립트가 로드되었을 때의 `onLoad` callback function을 등록할 수 있습니다.

* `onLoad` callback이 지정되지 않은 경우 자동으로 채팅 버튼이 설치됩니다. \(`init` 수행\)
* `onLoad` callback이 함수로 지정된 경우, 해당 함수의 첫 번째 파라미터 `init` 함수를 전달합니다.
* `onLoad` callback이 단순 string \(변수 이름\)으로 지정된 경우, `init`을 수행한 결과값이 해당 변수로 할당됩니다.

`onLoad` callback 함수는 아래 스키마의 `OnLoadCallback` 형식의 시그니처를 갖습니다.  
이 때, 첫 번째로 제공되는 파라미터가 CLOSER WebChat을 실행하는 `init` 함수입니다. 

* `init` 함수를 호출할 때 초기 환경설정 `WebChatInitOptions` 을 변경할 수 있습니다.
* `init` 함수의 반환값은 `WebChatControl`객체로, CLOSER WebChat의 동작 및 설정을 제어할 수 있습니다. 

#### API 타입 스키마

```typescript
type WebChatInitOptions = {
  userKey?: string;
  params?: any;
  enable?: boolean;
  defaultOpen?: boolean;
  theme?: WebChatThemeOption;
}

type WebChatThemeOption = {
  title?: string;
  description?: string;
  icon?: string; // url
  position?: 'left' | 'right' | 'top-left' | 'top-right';
  positionStrategy?: 'fixed' | 'absolute'; // css "position" strategy
  textColor?: string; //hex code, e.g. #000000
  primaryColor?: string; // hex code, e.g. #3b80e0
  primaryContrastTextColor?: string; // ex code, e.g. #ffffff
  pageMargin?: number | [number, number]; // [horizontal,vertical] margin if provided in array
  zIndex?: number; // button z-index
  defaultWindowSize?: {
    width?: number;
    height?: number;
  };
  greetingMessage?: string;
  enableResize?: boolean;
  buttonSize?: number;
  buttonIconSize?: string; // percentage string e.g. '50%'
}

type WebChatControl = {
  isOpen: boolean;
  isEnabled: boolean;
  params: Record<string, string | number | null | boolean>;
  userKey: string;
  theme: WebChatThemeOption;
  navigation: { 
    current: 'chat' | 'welcome' | 'setting' 
    stack: ('chat' | 'welcome' | 'setting')[] 
  };
  
  setOpen: (open: boolean) => void;
  setEnabled: (enable: boolean) => void;
  setParams: (params: Record<string, string | number | null | boolean>) => void;
  setUserKey: (userKey: string) => void;
  setTheme: (theme: WebChatThemeOption) => void;
  
  changeNavigation: (view: 'chat' | 'welcome' | 'setting' | 'back', action?: 'push' | 'pop') => void;
  startChat: (options?: { flowId?: number; params?: Params; override?: boolean }) => void;
}

type OnLoadCallback = (
  init: (options?: WebChatInitOptions) => WebChatControl
);

```

