---
title: "var, let, const 차이"
layout: single
categories:
  - Blog
tags:
  - JavaScript
  - var
  - let
  - const
---

## [ var, let, const 차이 ]

**1. 선언**

var - 중복 선언 가능

let, const - 중복 선언 불가능

**2. 초기화**

var, let - 초기화를 안 해도 된다.

const - 선언과 동시에 초기화를 해야 한다.

**3. 재할당**

var, let - 재할당 가능

const - 재할당 불가능

**4. 호이스팅**

var - 호이스팅 O

let, const - 호이스팅 X

**5.스코프(참조 가능한 영역)**

var - function

let, const - 블럭{}

### "각각 무엇을 의미할까?"

### **1. 선언 및 초기화**

```jsx
var v; //초기화를 안해도 된다.
var v = 'var'; //중복선언 가능

let l; //초기화를 안해도 된다.
let l = 'let'; //중복선언 불가능(Uncaught SyntaxError: Identifier 'l' has already been declared)

const c; //Error(Uncaught SyntaxError: Missing initializer in const declaration)
const c = 'const'; //중복선언 불가능(Uncaught SyntaxError: Identifier 'c' has already been declared)
```

### **2. 재할당**

```jsx
var v = 'var';
console.log(v); //output : var
v='var2';
console.log(v); //output : var2

let l = 'let';
console.log(l); //output : let
l = 'let2';
console.log(l); //output : let2

const c = 'const';
c= 'const2'; //Error(Uncaught TypeError: Assignment to constant variable.)
```

### **3. 호이스팅**

**호이스팅이란?**

javascript 엔진이 작동할 때(실행 컨텍스트 단계) var, function 등 선언 한 변수, 함수 등을 메모리에 저장하는 걸 의미합니다.

아래의 코드를 예를 들어보겠습니다.

```jsx
 example();

function example() {
	console.log('Test');
}
```

한 줄씩 차례대로 진행하면 위와 같은 코드는 오류가 발생해야 정상이지만 호이스팅이 발생하면서 example 함수를 메모리에 저장했기 때문에 오류가 발생하지 않습니다.

**var와 let, const 호이스팅 차이**

아래의 코드를 보면 var는 에러가 안 나고 let, const는 Uncaught ReferenceError가 발생하는 걸 확인할 수 있습니다.

```jsx
console.log(v)
var v = 'var';
//output : undefined

console.log(l)
let l = 'let';
//output : Uncaught ReferenceError: Cannot access 'l' before initialization

console.log(c)
const c = 'const';
//output : Uncaught ReferenceError: c is not defined
```

변수는 선언, 초기화, 할당의 단계를 걸쳐 선언되는데 이때 var와 let, const 차이가 발생합니다.

var의 경우 선언 시 선언과 초기화를 동시에 진행하고 (이때 undefined로 초기화 됩니다)

let, const의 경우 선언 시에 선언 단계만 진행합니다.(선언 단계에만 있을 때 **TDZ** 영역에 있다고 말합니다)

(※TDZ란? 초기화되지 않은 변수가 있는 영역)

호이스팅이 발생할때 TDZ에 있는 영역을 제외 하고 발생하기 때문에 위와 같은 차이가 발생합니다.

(※참고로 let, const, class는 TDZ에 영향을 받습니다.)
