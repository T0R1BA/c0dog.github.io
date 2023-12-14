---
title: "DOM 선택자"
excerpt: "DOM selector"
categories: JavaScript
tag: [JavaScript, selector]
toc: true
toc_label: "목록"
toc_icon: "bars"
toc_sticky: true
---

# DOM?
{: .notice--warning .text-center}

DOM은 문서 객체 모델(Document Object Model)의 약어로, 웹 페이지의 구조화된 표현을 프로그래밍적으로 조작할 수 있게 하는 인터페이스를 제공하는 API(응용 프로그래밍 인터페이스)입니다. DOM은 HTML, XML, 그리고 XHTML과 같은 문서의 구조를 표현하며, 각각의 요소에 JavaScript와 같은 스크립트 언어를 사용하여 동적으로 접근하고 조작할 수 있게 해줍니다.

간단히 말하면, DOM은 웹 페이지를 트리 구조로 표현하며, 각 요소에 대한 프로그래밍적인 제어를 가능하게 합니다. HTML 문서가 브라우저에 로드될 때, 브라우저는 이를 해석하여 DOM을 생성하고 이를 메모리에 저장합니다.

DOM은 다음과 같은 주요 특징을 갖고 있습니다:

계층 구조: DOM은 트리 구조로 표현되어 있어, 문서의 계층 구조를 반영합니다. HTML 요소들은 부모, 자식, 형제 관계로 연결돼 있습니다.

객체 지향적: DOM은 객체 지향적이며, 각 HTML 요소는 객체로 표현됩니다. 이 객체들은 프로퍼티와 메서드를 갖고 있어 이를 활용해 조작이 가능합니다.

동적으로 변경 가능: JavaScript를 사용하여 DOM을 동적으로 변경할 수 있습니다. 이를 통해 사용자와 상호작용하거나 웹 페이지를 동적으로 업데이트하는 데 사용됩니다.

이벤트 기반: DOM은 이벤트 기반 프로그래밍 모델을 제공하여, 사용자의 행동(클릭, 입력 등)에 대한 응답으로 동작하는 웹 애플리케이션을 만들 수 있도록 합니다.

# DOM-selector
{: .notice--warning .text-center}

## getElementById
{: .notice--success .text-center}

```html
<!-- getElementById는 DOM에서 특정 ID를 가진 HTML 요소를 찾아오는 메서드입니다. -->
<!-- getElementById는 문서 내에서 고유한 ID를 가진 요소를 찾아오기 때문에, ID는 유일해야 합니다. -->
<!-- 동일한 ID를 가진 요소가 여러 개 있다면, 함수는 첫 번째로 일치하는 요소를 반환합니다. -->
<h1 id="myHeading">안녕하세요!</h1>
<p id="myParagraph">이것은 단락입니다.</p>

<script>
// getElementById를 사용하여 특정 ID를 가진 요소 가져오기
var heading = document.getElementById('myHeading');
var paragraph = document.getElementById('myParagraph');

// 찾아온 요소에 스타일 적용
heading.style.color = 'blue';
paragraph.style.fontSize = '18px';

// 찾아온 요소의 내용 변경
heading.textContent = '안녕하세요, DOM!';
paragraph.textContent = '이것은 수정된 단락입니다.';
</script>
```

## getElementsByName
{: .notice--success .text-center}

```html
<!-- getElementsByName은 특정 이름(name) 속성을 가진 모든 HTML 요소를 가져오는 메서드입니다. -->
<!-- 이 메서드는 반환된 결과를 NodeList로 제공하며, NodeList는 유사 배열 객체로 각 요소에는 인덱스를 통해 접근할 수 있습니다. -->
<input type="text" name="username" placeholder="사용자 이름">
<input type="text" name="email" placeholder="이메일">
<button onclick="getElements()">요소 가져오기</button>

<script>
function getElements() {
  // getElementsByName을 사용하여 특정 이름(name)을 가진 모든 요소 가져오기
  var usernameInputs = document.getElementsByName('username');
  var emailInputs = document.getElementsByName('email');

  // NodeList를 배열로 변환하여 각 요소에 접근
  var usernameValue = usernameInputs[0].value;
  var emailValue = emailInputs[0].value;

  // 가져온 요소의 값을 출력
  console.log('사용자 이름:', usernameValue);
  console.log('이메일:', emailValue);
}
</script>
```

## getElementsByTagName
{: .notice--success .text-center}

```html
<!-- getElementsByTagName 메서드는 주어진 HTML 태그 이름을 가진 모든 요소를 가져옵니다. -->
<!-- 이 메서드는 반환된 결과를 NodeList로 제공하며, NodeList는 유사 배열 객체입니다. -->
<h2>과일 목록</h2>
<ul>
  <li>사과</li>
  <li>바나나</li>
  <li>딸기</li>
  <li>포도</li>
</ul>
<button onclick="getElements()">리스트 아이템 가져오기</button>

<script>
function getElements() {
  // getElementsByTagName을 사용하여 특정 태그 이름을 가진 모든 요소 가져오기
  var listItems = document.getElementsByTagName('li');

  // NodeList를 배열로 변환하여 각 요소에 접근
  for (var i = 0; i < listItems.length; i++) {
    var listItem = listItems[i];
    console.log('리스트 아이템:', listItem.textContent);
  }
}
</script>
```

## getElementsByClassName
{: .notice--success .text-center}

```html
<!-- getElementsByClassName 메서드는 주어진 클래스 이름을 가진 모든 HTML 요소를 가져오는 메서드입니다. -->
<!-- 이 메서드 또한 반환된 결과를 NodeList로 제공하며, NodeList는 유사 배열 객체입니다. -->
<head>
  <style>
    .highlighted {
      color: red;
      font-weight: bold;
    }
  </style>
</head>

<p class="highlighted">이 텍스트는 강조됩니다.</p>
<p>이 텍스트는 강조되지 않습니다.</p>
<button onclick="getElements()">강조된 요소 가져오기</button>

<script>
function getElements() {
  // getElementsByClassName을 사용하여 특정 클래스 이름을 가진 모든 요소 가져오기
  var highlightedElements = document.getElementsByClassName('highlighted');

  // NodeList를 배열로 변환하여 각 요소에 접근
  for (var i = 0; i < highlightedElements.length; i++) {
    var element = highlightedElements[i];
    console.log('강조된 요소:', element.textContent);
  }
}
</script>
```

## querySelector
{: .notice--success .text-center}

```html
<!-- querySelector 메서드는 주어진 CSS 선택자에 일치하는 첫 번째 HTML 요소를 가져오는 메서드입니다. -->
<!-- 이 메서드를 사용하면 더 유연하게 요소를 선택할 수 있습니다. -->
<head>
  <style>
    .highlighted {
      color: red;
      font-weight: bold;
    }
  </style>
</head>

<p class="highlighted">이 텍스트는 강조됩니다.</p>
<p>이 텍스트는 강조되지 않습니다.</p>
<button onclick="getElement()">강조된 요소 가져오기</button>

<script>
function getElement() {
  // querySelector을 사용하여 특정 CSS 선택자에 일치하는 첫 번째 요소 가져오기
  var highlightedElement = document.querySelector('.highlighted');

  // 가져온 요소에 스타일 적용
  highlightedElement.style.fontSize = '18px';

  // 가져온 요소의 내용 변경
  highlightedElement.textContent = '이 텍스트가 강조됩니다.';
}
</script>
```

## querySelectorAll
{: .notice--success .text-center}

```html
<!-- querySelectorAll 메서드는 주어진 CSS 선택자에 일치하는 모든 HTML 요소를 NodeList로 가져오는 메서드입니다. -->
<!-- 이 메서드를 사용하면 여러 요소를 선택할 수 있습니다. -->
<head>
  <style>
    .highlighted {
      color: red;
      font-weight: bold;
    }
  </style>
</head>

<p class="highlighted">이 텍스트는 강조됩니다.</p>
<p>이 텍스트는 강조되지 않습니다.</p>
<button onclick="getElements()">강조된 요소 가져오기</button>

<script>
function getElements() {
  // querySelectorAll을 사용하여 특정 CSS 선택자에 일치하는 모든 요소 가져오기
  var highlightedElements = document.querySelectorAll('.highlighted');

  // NodeList를 배열로 변환하여 각 요소에 접근
  highlightedElements.forEach(function(element) {
    // 가져온 요소에 스타일 적용
    element.style.fontSize = '18px';

    // 가져온 요소의 내용 변경
    element.textContent = '이 텍스트가 강조됩니다.';
  });
}
</script>
```

# form 태그 id, name으로 input value 가져오기
{: .notice--warning .text-center}

```html
<form action="#" name="myForm" id="formId">
    <input type="text" name="inputID" id="inputID"  value="test1"><br>
    <input type="text" name="inputName" id="inputName"  value="홍길동"><br>
    <input type="submit" value="제출">
</form>

<script>
    // form id로 input value 가져오기 (document.forms. 생략 가능)
    document.write('inputID 값 : ' + document.forms.formId.inputID.value + '<br>');
    document.write('inputName 값 : ' + document.forms.formId.inputName.value + '<br>');

    // form name로 input value 가져오기 (document.forms. 생략 가능)
    document.write('inputID 값 : ' + document.forms.myForm.inputID.value + '<br>');
    document.write('inputName 값 : ' + document.forms.myForm.inputName.value + '<br>');

    myForm.submit();
</script>
```

# element 접근 및 수정하기
{: .notice--warning .text-center}

```html
<script>
    var test1 = document.getElementById('test1');

    // 기존 요소 변경
    test1.innerHTML = '<h3 style="color:red;">추가한 HTML1</h3><h3 style="color:blue;">추가한 HTML2</h3>';

    // 기존 요소에 추가
    test1.innerHTML += '<h3 style="color:red;">추가한 HTML1</h3><h3 style="color:blue;">추가한 HTML2</h3>';

    // 텍스트만 변경
    test1.innerText = '텍스트 추가하는 방법';

    // 고유 속성 변경
    test1.value = '2';
    test1.userName = 'ellis';

    // 클래스 네임 수정
    test1.className ='testClass';

    // 현재 적용된 class 확인
    document.write('classList : ' + test1.classList + '<br>')
    console.log(test2.classList);
</script>
```