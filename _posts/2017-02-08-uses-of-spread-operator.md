---
layout: post
title: 스프레드 연산자(...) 사용 예
published: true
---

몇가지 스프레드 연산자의 사용 예 정리겸. 
 
> [6 Great Uses of the Spread Operator](https://davidwalsh.name/spread-operator)  
[Merge Object Properties with the Spread Operator](https://davidwalsh.name/merge-objects)

___

### Apply 대체
기존 `Function.prototype.apply` 사용시

```javascript
function doStuff (x, y, z) { }
var args = [0, 1, 2];
doStuff.apply(null, args);
```

but 스프레드 연산자 사용시 더 깔끔하고, `null`을 사용할 필요가 없다.

```javascript
doStuff(...args);
```

### Array 결합
기존에 있던 [다양한 Array 결합방법](https://davidwalsh.name/combining-js-arrays) 대신 아래와 같이 사용할 수 있다.

```javascript
arr1.push(...arr2) // Array의 끝에 arr2 추가
arr1.unshift(...arr2) //Array의 시작에 arr2 추가
```

시작, 끝뿐만이 아니라 아래와 같이 중간에 삽입도 가능하다.

```javascript
var arr1 = ['two', 'three'];
var arr2 = ['one', ...arr1, 'four', 'five'];

// ["one", "two", "three", "four", "five"]
```

### Array 복사

Array 복사를 위해 `Array.prototype.slice`를 사용해오곤 했는데, 스프레드 연산자를 통해 아래와 같이 복사할 수 있다.

```javascript
var arr = [1,2,3];
var arr2 = [...arr]; // like arr.slice()
arr2.push(4)
```
> 주의: Array안의 Object들은 여전히 참조형태다, 즉 모든게 복사되진 않는다.

### Array-like object를 Array로 변경

`Node List`, `arguments` 등의 Array-like object들을 Array로 변경할때 기존의 `Array.Prototype.slice` 사용 대신 아래와 같이 사용할 수 있다.

```javascript
[...document.querySelectorAll('div')]
``` 

arguments를 다음과 같이 Array로 얻을수도 있다.

```javascript
var myFn = function(...args) {
// ...
}
```

> 참고: `Array.from` 도 같은 일을 할 수 있다. IE는 지원 안됨.

### Math 사용시

`Math`의 함수들은 스프레드 연산자를 활용할 수 있는 좋은 예다.

```javascript
let numbers = [9, 4, 7, 1];
Math.min(...numbers); // 1
```

### 비구조화(Destructuring)

```javascript
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }
```

### 중복 제거

```javascript
const arr = [7, 3, 1, 3, 3, 7];
const arr2 = [...new Set(arr)] // [ 7, 3, 1 ]
```

> 참고: [Set](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Set)

### Object 결합

```javascript
const person = { name: 'David Walsh', gender: 'Male' };
const tools = { computer: 'Mac', editor: 'Atom' };

const summary = {...person, ...tools};
/*
Object {
  "computer": "Mac",
  "editor": "Atom",
  "gender": "Male",
  "name": "David Walsh",
}
*/
```

키가 중복시 마지막(오른쪽) Object의 값이 승리한다.

```javascript
onst person1 = { name: 'David Walsh', age: 33 };
const person2 = { name: 'David Walsh Jr.', role: 'kid' };

const merged = {...person1, ...person2}
/*
Object {
  "name": "David Walsh Jr.",
  "age": 33,
  "role": "kid",
}
*/
```

> `Object.assign`를 통해서도 같은 작업을 할 수 있다.  

> 이 문법은 아직 모든 브라우저에서 지원되지 않는다. Babel의 `transform-object-rest-spread` 플러그인을 사용하면 스프레드 연산자로 Object 결합이 가능하다.


