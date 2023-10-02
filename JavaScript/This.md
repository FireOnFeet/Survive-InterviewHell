# 📆 날짜: 2023-10-02

## 🎯 공통 질문: this란 무엇인가요?

### 나라's 답변:

---

## <!-- 답변 -->

### 슬기's 답변:

---

## 자바스크립트에서 this는 현재 컨텍스트의 실행 주체를 가리키는 키워드입니다. 그 주체는 함수가 어떻게 호출되었는지에 따라 달라집니다.

## 🎯 공통 질문: 함수에서의 this는 무엇을 가르키나요?

### 나라's 답변:

### 슬기's 답변:

함수에서의 this는 기본적으로 전역 객체를 가리킵니다. 브라우저 환경에서는 window 객체, Node.js환경에서는 global객체를 가리킵니다.

#### 슬기's 꼬리질문 : 함수가 'strict mode'에서 실행될 경우 this는 무엇을 가리키나요?

##### 슬기's 답변 :

undefined를 가리킵니다.

"strict mode는 ECMAScript 5(ES5)에서 도입된 기능으로, 자바스크립트의 오류를 잡기 쉽게 만들기 위해 몇몇 기존의 유연한 행동들을 제한하고 오류를 발생시키는 경우를 확대합니다. strict mode에서 함수의 this는 더 이상 자동으로 전역 객체를 참조하지 않습니다. 일반 함수에서 this가 특정 객체로 바인딩되지 않을 경우, 그 값은 undefined가 됩니다. 이러한 행동은 개발자가 실수로 전역 객체를 수정하는 것을 방지하고, 코드의 안정성과 예측 가능성을 높이기 위한 것입니다. 예를 들어, strict mode가 아닌 일반 모드에서는 this가 암묵적으로 전역 객체를 가리키므로, 개발자가 실수로 전역 변수를 변경하거나 오염시킬 위험이 있습니다."

## 🎯 공통 질문: 메서드 호출시 this는 무엇을 가르키나요?

### 나라's 답변:

### 슬기's 답변:

메서드 호출시 this는 해당 메서드를 소유하고 있는 객체를 가리킵니다.

```
const obj = {
  name: "슬기",
  greet: function() {
    console.log("안녕하세요, " + this.name);
  }
};

obj.greet();  // 여기서 this는 obj를 가리킵니다.

```

## 🎯 공통 질문: 콜백함수에서의 this는 무엇을 가르키나요?

### 나라's 답변:

### 슬기's 답변:

콜백함수의 경우 기본적으로 함수이기에 this는 전역 객체를 가리킵니다.
일반함수로서의 콜백일 경우 전역 객체를 가리키지만, 객체의 메서드로서의 콜백이 되면 그 객체를 가리키게됩니다.

일반함수

```
function callback() {
  console.log(this);  // window (브라우저 환경)
}
setTimeout(callback, 1000);

```

객체로서의 함수

```
const obj = {
  callback: function() {
    console.log(this);  // obj
  }
};
setTimeout(obj.callback, 1000);

```

## 🎯 공통 질문: 화살표 함수의 this는 무엇을 가르키나요?

### 나라's 답변:

### 슬기's 답변:

화살표 함수는 자체적인 this바인딩을 갖지 않기에 화살표 함수가 생성될 때의 상위 스코프의 this의 값을 가리키게됩니다.

## 🎯 공통 질문: 생성자함수의 this는 무엇을 가르키나요?

### 나라's 답변:

### 슬기's 답변:

새롭게 생성된 인스턴스를 가리킵니다.

## 🔗 나라's 꼬리질문 : this바인딩은 언제 지정되나요?

### 나라's 답변:

### 슬기's 답변:

this 바인딩은 함수가 호출될 때 동적으로 결정됩니다. 어떻게 호출하느냐에 따라 this의 값이 달라집니다.

## 🔗 나라's 꼬리질문 : this를 명시적으로 바인딩하는 방법을 얘기해주세요. 또한 명시적으로 바인딩 되지 않았다면 어떻게 되나요?

### 나라's 답변:

### 슬기's 답변:

call, apply, bind 메서드를 사용하여 this의 값을 원하는 객체로 설정할 수 있습니다.
반대로 명시적으로 바인딩되지않는 경우 this는 함수 호출방식에 따라 동적으로 바인딩 됩니다.

call과 apply는 첫번째 인자에서 this로 하고자하는 argument를 넘기고, call의 경우 이후 인자들을 순서대로 함수의 파라미터로 전달하는 방식이며 apply는 이후 인자를 배열로 한번에 넘긴다는 특징이있습니다.
반면 bind의 경우 this를 바인딩할 수 있지만, 함수를 호출하지않고 this값을 바인딩한 새로운함수를 생성하여 반환한다는 특징이있습니다.

## 🔗 나라's 꼬리질문 : this바인딩을 어떨 때 사용할 수 있을까요? 예시를 하나 만들어주세요

### 나라's 답변:

### 슬기's 답변:

이벤트 핸들러에서 this를 바인딩 해야하는 경우가 있습니다.
이경우 this를 바인딩하지않는다면, 해당 버튼에 바인딩 된 이벤트 핸들러 내에서 this는 클릭된 버튼 요소를 가리키지 않을 수 있습니다. 대신, 다른 컨텍스트나 전역 객체를 가리킬 가능성이 있습니다.이 경우 bind 를 이용해 바인딩을 해준다면, 버튼을 가리키게 됩니다.

## 🔗 슬기's 꼬리질문 : 바인딩이란 무엇인가요?

### 나라's 답변:

### 슬기's 답변:

식별자와 값을 연결하는 과정을 말합니다. 변수를 선언하게되면, 변수 이름과 해당 메모리 주소가 연결되는 것 같이 this로 가리킬 객체를 바인딩하는것을 말합니다.

## 🔗 슬기's 꼬리질문 : arrow-function이란 무엇인가요?

### 나라's 답변:

### 슬기's 답변:

es6에서 도입된 새로운 함수 표현 방식으로, 간결한 문법 및 this바인딩을 생성하지 않고 상위스코프의 this 값을 캡쳐한다는 특징이 있습니다.

## 🔗 슬기's 꼬리질문 : 왜 arrow-function이 나오게 된건가요?

### 나라's 답변:

### 슬기's 답변:

간단한 문법이기도 하며, this 바인딩의 문제가 생기기에 콜백 함수 경우 this 바인딩을 하려면 call, apply, bind와 같은 작업을 해주어야하는데, 이런 경우 this 를 쉽게 바인딩하게 하기위해 생겨진 것 같습니다.

#### 슬기's 꼬리질문 : 언제 arrow-function을 사용하지 못할까요?

##### 슬기's 답변 :

화살표함수가 prototype의 속성을 갖지 않기에 생성자함수 혹은 prototype 메서드를 정의할 경우에는 사용할 수 없습니다.
또한 arguments객체를 갖지않기에 arguments 객체에 접근이 불가합니다.

## 🔗 슬기's 꼬리질문 : 왜 arrow-function은 this 바인딩이 상위 컨텍스트의 this를 참조하게될까요?

### 나라's 답변:

### 슬기's 답변:

this 바인딩 개념이 존재하지않으며, 스코프 체인에 따라 상위 스코프의 this를 캡쳐하는 동작 방식이기 때문입니다.

## 🔗 슬기's 꼬리질문 : 개발을 할 때 arrow-function과 function 중 어떤 걸 더 선호하나요 ? 이유는 무엇인가요?

### 나라's 답변:

### 슬기's 답변:

저는 arrow-function을 선호합니다.
먼저, 간결하기도 하며 this 바인딩을 고민하며 코드를 구현하지 않아도 된다는 점 때문입니다.

## 🔗 GPT's 꼬리질문 : 어떤 상황에서 this의 값이 undefined가 될 수 있나요?

### 나라's 답변:

### 슬기's 답변:

strict mode 특성상 this는 더 이상 자동으로 전역 객체를 참조하지 않기에, 함수가 'strict mode'에서 실행될 경우 undefined가 될 수 있습니다.

## 🔗 GPT's 꼬리질문 : 이벤트 핸들러 내부에서의 this는 무엇을 가리키나요? 그리고 이를 변경하려면 어떻게 해야하나요?

### 나라's 답변:

### 슬기's 답변:

이벤트 핸들러 내부에서 this는 해당 이벤트를 가리킵니다. 이를 원하는 객체로 바인딩 하기 위해서는 call, apply, bind 혹은 화살표 함수를 이용하여 바인딩 할 수 있습니다.

## 🔗 GPT's 꼬리질문 : this의 값이 예상과 다를 때, 어떻게 디버깅하고 문제를 해결하나요?

### 나라's 답변:

### 슬기's 답변:

먼저 호출 방식을 확인한 후 console.log를 출력해보며 어떤 this가 찍혔는지 가설 검증 방식으로 디버깅 할 것 같습니다.
만약 전역객체가 찍혔다면, 어디서 바인딩이 안된것인지 내 예상 동작대로하려면 call, apply, bind메서드로 할 수 있는지 이런식으로 적용해 볼 것 같습니다.

## 🔗 GPT's 꼬리질문 : ES6 클래스 내부에서의 this는 어떻게 동작하나요? 클래스 메서드와 클래스 필드에서의 this의 차이점은 무엇인가요?

### 나라's 답변:

### 슬기's 답변:

클래스의 생성자 및 메서드에서의 this는 해당 클래스의 인스턴스를 참조합니다.

## 🔗 GPT's 꼬리질문 : 프로토타입 메서드에서의 this는 어떻게 동작하나요?

### 나라's 답변:

### 슬기's 답변:

프로토타입 메서드 내에서의 this는 해당 메서드를 호출한 객체 인스턴스를 참조합니다.

```
function Person(name) {
    this.name = name;
}

Person.prototype.sayHello = function() {
    console.log(`Hello, my name is ${this.name}.`);
};

const alice = new Person("Alice");
alice.sayHello(); // Outputs: "Hello, my name is Alice."

```

---

#### REFERENCE

##### 나라

<!-- 답변 -->

##### 슬기

- this

  함수가 만들어졌을 때, 뒤에서는 `this`라 불리는 키워드가 만들어집니다. `this`는 함수가 동작하는 곳에 있는 오브젝트와 연결해줍니다.
  `this` 키워드의 값은 그 함수 자체와는 상관이 없습니다. 함수가 어떻게 불려지는지가 `this`의 값을 결정합니다.

- 기본 "this" 컨텍스트

  this의 값은 어떤 것이 될지 예측할 수 있을까요? 기본 값으로, this는 언제나 전역 스코프의 root을 참조하는 window Object가 됩니다. 만일, 스크립트가 strict mode("use strict") 내에서 작동하고 있다면, this는 undefined일 것입니다.

- 오브젝트 리터럴(Object literals)

  ```
  var myMethod = function () {
  console.log(this);
  };

  var myObject = {
  myMethod: myMethod
  };
  ```

  물론, 여전히 `this`의 값은 우리가 함수를 어떻게 호출하냐에 따라 달렸습니다.

  코드 안의 `myObject`는 `myMethod`라 불리는 프로퍼티를 갖습니다. 이 프로퍼티는 `myMethod` 함수를 가리킵니다. `myMethod` 함수가 글로벌 스코프로부터 호출됐을 때, `this`는 window object를 참조합니다. `myObject`의 메소드로서 호출됐을 때는, `this`가 `myObject`를 참조합니다.

  ```
  myObject.myMethod() // this === myObject
  myMethod() // this === window
  ```

  이러한 형식은 **묵시적 바인딩(implicit binding)** 이라 불립니다.

- 명시적 바인딩(Explicit binding)

  함수에 명시적으로 컨텍스트를 바인딩할 때, 그것을 명시적 바인딩이라 합니다. 이러한 동작은 주로 `call()` 메소드와 `apply()` 메소드에 의해 이뤄집니다.

  ```
  var myMethod = function () {
  console.log(this);
  };

  var myObject = {
  myMethod: myMethod
  };

  myMethod() // this === window
  myMethod.call(myObject, args1, args2, ...) // this === myObject
  myMethod.apply(myObject, [array of args]) // this === myObject
  ```

  명시적인 바인딩은 묵시적 바인딩보다 우위를 갖게 됩니다.

- 하드 바인딩(Hard binding)

  하드 바인딩은 `bind()` (ES5)으로 가능합니다. `bind()` 메소드는 우리가 지정한 `this` 컨텍스트를 가진 기존 함수를 불러오기 위해 하드코딩된 새로운 함수를 반환합니다.

  ```
  myMethod = myMethod.bind(myObject);

  myMethod(); // this === myObject
  ```

  하드바인딩은 명시적 바인딩보다 우위를 갖게 됩니다.

- 'New' 바인딩(New binding)

  ```
  function foo(a) {
  this.a = a;
  }

  var bar = new foo( 2 );
  console.log( bar.a ); // 2
  ```

  새로운 new 인스턴스를 참조하는 함수가 호출되었을 때, `this`가 만들어집니다.

  함수가 new와 함께 호출되었을 때는 묵시적, 명시적 또는 하드 바인딩을 신경쓰지 않습니다. 이 때는 그냥 새로운 인스턴스인 새로운 컨텍스트를 만들어냅니다.

- call(), apply(), bind() 이해하기

  자바스크립트에서 함수들은 오브젝트들이고, 위 3개의 메소드는 함수의 호출을 제어하기 위해 사용됩니다. `call()`과 `apply()`는 ECMAScript 3에서 소개되었고, `bind()` 메소드는 ECMAScript 5에서 추가되었습니다.

- 사용 예시
  함수를 즉시 호출하기 위해서 `call()` / `apply()` 메소드를 사용할 수 있습니다. `bind()` 는 함수가 나중에 실행됐을 때도 원본 함수를 호출할 때 갖는 올바른(correct) 컨텍스트(**this**)가 bind된 함수를 반환합니다. 그래서 `bind()`는 특정 이벤트에서 함수가 나중에 호출될 필요가 있을 때, 유용합니다.

---
