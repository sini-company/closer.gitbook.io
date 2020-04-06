---
description: 템플릿 문법에서 함께 사용할 수 있는 도우미 함수들을 소개합니다.
---

# 템플릿 도우미 함수 \(Helper Function\)

### **RAND\(from, to\) : Number**

* `from`과 `to`사이의 숫자를 반환합니다. \(from, to 모두 정수로 입력된 경우\)
* e.g\) `{{RAND(1,10)}}` -&gt; `6` \(1~10 사이의 값\)



### RAND\(...items\) : String

* `items` 값 중 하나를 반환합니다.
* e.g\) `{{RAND("철수", "영희"}}` -&gt; `철수` \(철수, 영희 둘 중 하나\)



### JOSA\(noun, josa?: "은" \| "는" \| "이" \| "가" \| "을" \| "를"\) 

* 한글 명사 `noun` 에 적절한 조사를 변환해주는 도우미 함수입니다. 두 번째 인자에 `은/는`, `이/가`, `을/를` 조합 중 이용하고자 하는 조사를 한 글자로 작성해주세요.
* 예시\)
  * `{{JOSA("멍멍이","이")}}` -&gt; `멍멍이가`
  * `{{JOSA(params.product, "을"}}` , `{ "product": "떡볶이" }`-&gt; `떡볶이를`

### 

### FORMAT\(value, option?\)

주어진 value를 원하는 형태로 출력합니다. 주로 number값을 출력할 때 이용합니다.

* `option`은 출력 형태를 지정합니다. 지정되지 않은 경우 [Javascript의 toLocaleString 결과값](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object/toLocaleString)을 이용합니다.
* 예시
  * `{{FORMAT(10000)}}` -&gt; `10,000`
  * `{{FORMAT("01234.5")}}` -&gt; `1,234.5` \(number string은 number로 변환됩니다.\)
  * `{{FORMAT("안녕하세요")}}` -&gt; `안녕하세요` \(plain string은 아무런 변화가 없습니다.\)
  * `{{FORMAT(1230974, "0.0a")}}` -&gt; `1.2m`

{% hint style="info" %}
Number formatting에는 Numeral.js 라이브러리를 이용하고 있습니다.  
이용 가능한 포매팅 옵션을 알아보려면 다음 링크를 참고하세요.

\(영문\) [http://numeraljs.com/\#format](http://numeraljs.com/#format) 
{% endhint %}



### TRUNCATE\(value, length, omission?\) <a id="truncate"></a>

주어진 문자열 `value`를 원하는 길이 `length` 만큼 자르는 함수입니다.

* `omission`: 문자열이 지정한 길이를 넘을 때 표시하는 말줄임표를 설정합니다. 기본값은 `''`입니다.
* 예시
  * `{{FORMAT("ABCDEFGHIJKLMNOP", 10}}` -&gt; `ABCEDFGHIJ`
  * `{{FORMAT("ABCDEFGHIJKLMNOP", 10, "..."}}` -&gt; `ABCEDFG...`

### \*\*\*\*

### **DATE\(value?, format?, timezone?\)**

날짜를 출력하는 함수입니다. 아무것도 지정하지 않을 시 현재 시간을 ISO Date String으로 반환합니다.

* `value`: ISO date string or UNIX timestamp \(선택\)
* `format?`: 날짜 표현 방식을 설정 \(선택\)
* `timezone?`: 날짜를 표시할 기준 시간대를 설정 \(선택\)
* 예시
  * `{{DATE()}}` 또는 `{{DATE(null)}}` =&gt; `2018-12-07T05:47:14.667Z` \(ISO Date, UTC timezone\)
  * `{{DATE("2018-12-07","YYYY.MM")}}`  =&gt; `2018.12` 
  * `{{DATE("2018-12-07T05:47:14.667Z", "YYYY년 MM월 DD일 HH시 mm분", "Asia/Seoul")}}`  =&gt; `2018년 12월 07일 14시 47분` 

{% hint style="info" %}
현재 시간을 기준으로 format, timezone을 적용하려면 value에 null을 입력하세요.  
e.g.\) `{{DATE(null, "YYYY-MM-DD")}}`
{% endhint %}

{% hint style="info" %}
Date manipulation에는 Moment.js 라이브러리를 이용하고 있습니다.  
이용 가능한 시간대와 포매팅 방식을 더 자세히 알아보려면 다음 링크를 참고하세요.

\(영문\) [https://momentjs.com/docs/\#/displaying/format/](https://momentjs.com/docs/#/displaying/format/)  
\(영문\) [https://momentjs.com/timezone/](https://momentjs.com/timezone/)
{% endhint %}

