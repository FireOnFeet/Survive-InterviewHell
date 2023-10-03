# 📆 날짜: 2023-10-02

## 🎯 공통 질문: this란 무엇인가요?

### 나라's 답변:

---

## JavaScript에서 this는 현재 실행 컨텍스트에 바인딩되는 것으로 값이 동적으로 바인딩이 이뤄지며 함수가 호출하는 방식에 따라 참조가 바뀝니다.

### 슬기's 답변:

---

## <!-- 답변 -->

## 🎯 공통 질문: 함수에서의 this는 무엇을 가르키나요?

### 나라's 답변:

보통 함수에서의 this는 전역객체를 가르킵니다.

### 슬기's 답변:

## 🎯 공통 질문: 메서드 호출시 this는 무엇을 가르키나요?

### 나라's 답변:

메서드를 호출한 주체를 참조합니다.

#### 나라's 꼬리질문 : 그렇다면 아래의 코드에서의 this는 어떤것을 가르키게될까요?

```javascript
var obj = {
  methodA: function () {
    console.log(this);
  },
  inner: {
    methodB: function () {
      console.log(this);
    },
  },
};

obj.inner.methodB();
```

methodB의 호출주체인 obj에서의 inner를 가르키게됩니다. 결과값은 methodB의 값이 나오게 될 것이라고 예상됩니다.

### 슬기's 답변:

## 🎯 공통 질문: 콜백함수에서의 this는 무엇을 가르키나요?

### 나라's 답변:

콜백함수로 호출되었을 때 해당 메서드를 소유한 객체를 참조하게 됩니다.
this를 바인딩하지 않거나 일반함수로 호출되었다면 this는 전역객체를 참조하게됩니다.
화살표함수로 정의되었다면 주변 스코프에 의해서 this값이 결정되게 될 것입니다.

### 슬기's 답변:

## 🎯 공통 질문: 화살표 함수의 this는 무엇을 가르키나요?

### 나라's 답변:

화살표 함수의 컨텍스트에서의 상위 컨텍스트의 this값을 가르킵니다.

### 슬기's 답변:

## 🎯 공통 질문: 생성자함수의 this는 무엇을 가르키나요?

### 나라's 답변:

생성자 함수로 생성되어질 인스턴스의 값을 가르킵니다.

### 슬기's 답변:

## 🔗 나라's 꼬리질문 : this바인딩은 언제 지정되나요?

### 나라's 답변:

this바인딩은 함수가 호출될 때 지정되어집니다.

### 슬기's 답변:

## 🔗 나라's 꼬리질문 : this를 명시적으로 바인딩하는 방법을 얘기해주세요. 또한 명시적으로 바인딩 되지 않았다면 어떻게 되나요?

### 나라's 답변:

this를 명시적 바인딩을 하는 방법은 바인딩 메서드를 사용하면 됩니다.
대표적으로 call, apply, bind메서드가 존재합니다.
call과 apply, bind메서드 셋 다 첫 인자값에 this Argument가 지정됩니다.
하지만 call메서드는 두번째 인자값에 하나씩 전달하며 apply는 인자를 배열로 넘겨서 함수를 호출합니다
bind메서드는 사용시 바인딩된 this값으로 함수가 생성됩니다.
명시적으로 바인딩처리를 하지 않았다면 호출방식에 따라 this바인딩이 이뤄집니다.

### 슬기's 답변:

## 🔗 나라's 꼬리질문 : this바인딩을 어떨 때 사용할 수 있을까요? 예시를 하나 만들어주세요

### 나라's 답변:

예를들어 장바구니 객체가 존재한다고 했을 때 상품 추가 메서드가 존재합니다.
이때 상품 객체를 장바구니 객체에 추가할려고 했을 때 상품객체를 call메서드를 사용하여 바인딩할 수 있습니다.

```javascript
const cart = {
  items: [],
  addItem: function (item) {
    this.items.push(item);
    console.log(`${item}이 장바구니에 추가되었습니다.`);
  },
};
const product = {
  name: "상품 1",
};
function addCart() {
  cart.addItem(this.name);
}

addCart.call(product);
```

### 슬기's 답변:

## 🔗 슬기's 꼬리질문 : 바인딩이란 무엇인가요?

### 나라's 답변:

프로그램의 어떤 기본단위가 가질 수 있는 구성요소의 구체적인 값, 성격을 확정하는 것.
즉 변수명, 함수가 위치한 메모리에 주소값을 연결하는 것

### 슬기's 답변:

## 🔗 슬기's 꼬리질문 : arrow-function이란 무엇인가요?

### 나라's 답변:

ES6에서 도입된 문법이며 function키워드 대신 함수를 간단히 표현할 수 있는 표현입니다.
화살표함수는 함수가 실행될 때 this를 정의하며 화살표 함수의 this바인딩은 상위스코프의 this를 참조합니다.

### 슬기's 답변:

## 🔗 슬기's 꼬리질문 : 왜 arrow-function이 나오게 된건가요?

### 나라's 답변:

보다 간편하게 함수를 사용하기 위함과 일반함수로 호출하였을 때 this값이 전역객체를 참조하는 오류를 수정하기 위하여 화살표함수가 등장했습니다.

### 슬기's 답변:

## 🔗 슬기's 꼬리질문 : 왜 arrow-function은 this 바인딩이 상위 컨텍스트의 this를 참조하게될까요?

### 나라's 답변:

화살표 함수에서는 this바인딩이라는 것이 존재하지 않으며 그에따라 this값을 참조하기위해 실행 컨텍스트의 스코프체인을 통해서 this를 찾기 때문입니다.

### 슬기's 답변:

## 🔗 슬기's 꼬리질문 : 개발을 할 때 arrow-function과 function 중 어떤 걸 더 선호하나요 ? 이유는 무엇인가요?

### 나라's 답변:

arrow-function으로 사용하는 것을 선호합니다. (사실 선언식과 섞어서 썼지만 앞으로는 그러지 않을것이기에 이렇게 답변합니다 ^0^) 이유는 선언식에서의 this바인딩을 위해서 명시적 바인딩처리를 하지 않을 수 있기 때문입니다.

### 슬기's 답변:

## 🔗 GPT's 꼬리질문 : 어떤 상황에서 this의 값이 undefined가 될 수 있나요?

### 나라's 답변:

strict mode에서 this값을 사용했을 때입니다.
이유는 strict mode에서는 this값이 전역객체를 참조하지 않기 때문입니다.

### 슬기's 답변:

## 🔗 GPT's 꼬리질문 : 이벤트 핸들러 내부에서의 this는 무엇을 가리키나요? 그리고 이를 변경하려면 어떻게 해야하나요?

### 나라's 답변:

기본적으로 이벤트를 처리하는 DOM요소를 가리킵니다.
이를 변경하려면 bind메서드 처리를 하여 원하는 객체를 가리키게 할 수 있으며 또는 화살표함수를 사용하여 처리할 수 있습니다.

### 슬기's 답변:

## 🔗 GPT's 꼬리질문 : this의 값이 예상과 다를 때, 어떻게 디버깅하고 문제를 해결하나요?

### 나라's 답변:

우선 strict mode인지 인지하며 이후 console.log처리를 하여 this값이 어떤 값이 나오는지를 확인합니다.

### 슬기's 답변:

## 🔗 GPT's 꼬리질문 : ES6 클래스 내부에서의 this는 어떻게 동작하나요? 클래스 메서드와 클래스 필드에서의 this의 차이점은 무엇인가요?

### 나라's 답변:

ES6에서의 클래스 내부의 this는 클래스의 인스턴스를 참조하게 됩니다. constructor나 getter, setter내에서 this를 사용한다면 해당 클래스의 인스턴스 값을 참조하게 됩니다.

클래스 메서드에서의 this는 메서드를 "호출한 객체"의 인스턴스를 참조하며 호출할 때 동적으로 바인딩되어집니다.

클래스 필드에서의 this는 필드에 속한 인스턴스를 참조하게 되며 클래스의 인스턴스 값에 값을 추가하는 방식이 됩니다. 즉 다른 컨텍스트에서 호출하여도 this값은 변경되지않습니다.

```javascript
class Component {
  constructor(name) {
    this.name = name;
  }

  printName() {
    console.log(this.name);
  }

  field = () => {
    console.log(this.name);
  };
}

const component = new Component("ComponentA");
component.printName(); //
component.field();
```

### 슬기's 답변:

## 🔗 GPT's 꼬리질문 : 프로토타입 메서드에서의 this는 어떻게 동작하나요?

### 나라's 답변:

프로토타입의 메서드에서 this는 동적으로 바인딩, 즉 호출한 객체 인스턴스에 의해서 this바인딩됩니다.

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.printName = function () {
  console.log(this.name);
};
const nara = new Person("Nara"); // Nara
const seulgi = new Person("Seulgi"); // Seulgi
```

### 슬기's 답변:

---

#### REFERENCE

##### 나라

[EventHandler에서의 this값](https://developer.mozilla.org/ko/docs/Web/API/EventTarget/addEventListener#%EC%98%88%EC%A0%9C)

- this?
  - this는 현재 실행 컨텍스트에 바인딩되는 것으로 값이 동적으로 바인딩이 이뤄지며 함수가 호출하는 방식에 따라 참조가 바뀝니다.
  - 호출되는 방식에 따라 달라지는 this
    - 일반함수에서의 this : 전역객체
    - 메서드 호출시 this : 호출한 주체를 참조
    - 콜백함수에서의 this : 호출되었는 메서드에서의 객체, 없다면 전역객체를 가리킴.
    - 화살표함수에서의 this : 상위 컨텍스트의 this값
    - 생성자함수의 this : 생성되어질 인스턴스의 값
  - 바인딩? -> 변수명, 함수가 위치한 메모리에 주소값을 연결하는 것
  - this바인딩은 실행 컨텍스트가 활성화 될 때만 한다! === 함수가 호출될 때 실행 컨텍스트가 만들어진다 === this는 함수가 호출될 때 결정된다.
  - strict mode에서는 this가 전역객체를 참조하지 않기에 함수에서 this나 전역에서 this를 사용한다면 undefined가 출력

##### 슬기

<!-- 답변 -->

---
