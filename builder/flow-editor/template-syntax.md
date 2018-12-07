# 템플릿 문법\(Template Syntax\)

노드를 정적인 데이터들로만 작성하면 동적으로 변경되는 사용자 파라미터에 대응하는 Flow를 작성할 수 없습니다. 동적으로 변하는 상황에 대응하기 위해 CLOSER에서는 각 Node를 작성할 때 사용할 수 있는 [템플릿 엔진](https://en.wikipedia.org/wiki/Template_processor)을 제공합니다.

## 파라미터 사용하기 <a id="use-parameter"></a>

템플릿은 정해진 위치에 파라미터를 주입할 수 있는 금형에 비유할 수 있습니다. 봇 빌더에서 동적인 파라미터가 필요한 공간에 중괄호 2개로 감싸진 파라미터 삽입해 놓으면 실제 봇이 사용자 요청을 처리할 때 다음과 같은 결과를 반환합니다. 만일 템플릿에 입력된 파라미터가 존재하지 않는 경우 템플릿 엔진은 빈 문자열을 반환합니다.

* **템플릿**

  ```text
  입력하신 전화번호는 {{phoneNumber}}입니다.
  {{reservationDate}}에 연락드리겠습니다.
  ```

* **입력받은 파라미터**

  ```javascript
  { phoneNumber: '010-1234-5678' }
  ```

* **결과**

  ```text
  입력하신 전화번호는 010-1234-5678입니다.
  에 연락드리겠습니다.
  ```

만약 중괄호를 그대로 사용할 때에는 `{{{{raw}}}}`을 이용합니다.

* **템플릿**

  ```text
  저는 {{{{raw}}}}{{중괄호를 쓰고 싶어요}}{{{{/raw}}}}
  ```

* **결과**

  ```text
  저는 {{중괄호를 쓰고 싶어요}}
  ```

### 오브젝트 혹은 배열에 접근 <a id="access-object-and-array"></a>

파라미터가 오브젝트나 배열인 경우 JavaScript와 Handlebars의 오브젝트 경로 문법을 지원합니다.

* **템플릿**

  ```text
  {{poets[0]}}과 {{poets.[1]}}과 {{novel.author}}
  ```

* **입력받은 파라미터**

  ```javascript
  {
    poets: ['김소월', '유치환', '김수영'],
    novel: {
      author: '김동인',
      title: '감자'
    }
  }
  ```

* **결과**

  ```text
  김소월과 유치환과 김동인
  ```

템플릿 엔진은 사용자 정의 파라미터 외에도 [예약 파라미터](parameter.md#reserved-parameters)를 사용할 수 있으며, 나아가 더 다양하고 복잡한 로직을 작성할 수 있는 [템플릿 함수](template-syntax.md#template-functions)를 제공합니다.

### 배열 다루기 <a id="array-to-cards"></a>

배열 타입의 파라미터는 경로에 `[i]`를 활용하면 배열의 각 항목에 대해 값이 생성됩니다.

예를 들어 [SWAPI](https://swapi.co/)에서 스타워즈 우주선 목록 배열을 가져오는 API를 사용해 카드형 메시지를 출력해보겠습니다. HTTP요청노드에서 [https://swapi.co/api/starships](https://swapi.co/api/starships) 에 GET요청을 보내면 응답값은 예약 파라미터인 `{{fetch.data}}`에, 우주선 목록의 배열은 `{{fetch.data.results}}`에 저장됩니다. 이때 `{{fetch.data.results[i]}}`에 대해 카드를 생성하면 각 우주선에 대해 카드가 생성됩니다.

* **템플릿**

  ![&#xBC30;&#xC5F4;&#xC744; &#xCE90;&#xB7EC;&#xC140; &#xBA54;&#xC2DC;&#xC9C0;&#xB85C; &#xBC14;&#xAFB8;&#xAE30; &#xD15C;&#xD50C;&#xB9BF;](../../.gitbook/assets/array-to-cards-template.png)

* **입력받은 파라미터**

  ```javascript
  // GET https://swapi.co/api/starships
  {
    fetch: {
      data: {
          count: 37,
          next: 'https://swapi.co/api/starships/?page=2',
          previous: null,
          results: [
              {
                  name: 'Executor',
                  model: 'Executor-class star dreadnought',
                  manufacturer: 'Kuat Drive Yards, Fondor Shipyards',
            // ...
                  url: 'https://swapi.co/api/starships/15/'
              },
          // ...
        }
      }
    }
  ```

* **결과**

  ![&#xBC30;&#xC5F4;&#xC744; &#xCE90;&#xB7EC;&#xC140; &#xBA54;&#xC2DC;&#xC9C0;&#xB85C; &#xBC14;&#xAFB8;&#xAE30; &#xACB0;&#xACFC;](../../.gitbook/assets/array-to-cards-result.png)

## 템플릿 함수 \(Template Functions\) <a id="template-functions"></a>

CLOSER에서는 템플릿 문법으로 [Handlebars.js](http://handlebarsjs.com/)의 기본 문법을 지원합니다.

이 문서에서는 자주 사용되는 문법을 예시와 함께 소개합니다. 자세한 문법은 [Handlebars.js](http://handlebarsjs.com/) API문서를 참조해주세요.

### if-else, unless 구문

* **템플릿**

  ```text
  {{#if monkey}}원숭이 엉덩이는 빨개{{/if}}
  {{#if red}}빨간 건 사과{{/if}}
  {{#if apple}}
    {{apple}}는 맛있어
  {{else}}
    맛있으면 {{banana}}
  {{/if}}
  {{#unless mango}}{{banana}}는 길어{{/unless}}
  ```

  **입력받은 파라미터**

  ```javascript
  { monkey: '원숭이', apple: '사과', banana: '바나나' }
  ```

* **결과**

  ```javascript
  원숭이 엉덩이는 빨개

    사과는 맛있어
  바나나는 길어
  ```

### each, with

* **템플릿**

  ```text
  {{#each poets}}{{this}}{{#unless @last }}과 {{/unless}}{{/each}}은 시인이고,
  {{#with novel}}{{author}}은 <{{title}}>를 썼다.{{/with}}
  ```

* **입력받은 파라미터**

  ```text
  {
    poets: ['김소월', '유치환', '김수영'],
    novel: {
      title: '감자',
      author: '김동인'
    }
  }
  ```

* **결과**

  ```text
  김소월과 유치환과 김수영은 시인이고,
  김동인은 <감자>를 썼다.
  ```

## 템플릿 문법에 오류가 발생한 경 <a id="on-error"></a>

작성된 노드가 제대로 동작하지 않을 수 있기 때문에 템플릿 엔진 사용시에는 각별한 주의가 필요합니다. 만약 오류가 발생할 경우 빈 문자열을 반환합니다.

* **템플릿**

  ```text
  {{#if}}if를 닫지 않음
  ```

* **결과** 

  ```text

  ```

