# TypeScript 기초 문법 완전 정복

## 목차
1. [주석 작성법](#1-주석)
2. [변수 선언](#2-변수의-선언)
3. [원시 타입](#3-원시-타입-변수)
4. [참조 타입](#4-참조-타입-변수)
5. [얕은 복사와 깊은 복사](#5-얕은-복사-깊은-복사)
6. [조건문과 반복문](#6-조건문과-반복문)

---

## 1. 주석

TypeScript에서 주석은 코드의 가독성을 높이고 설명을 추가하는 중요한 요소입니다. 인터프리터는 주석을 무시하므로 개발자만 볼 수 있습니다.

```tsx
// 한 줄 주석
console.log("실행되는 코드");

/* 
 * 여러 줄 주석
 * 긴 설명이 필요할 때 사용
 */
console.log("여러 줄 주석 예시");
```

---

## 2. 변수의 선언

TypeScript는 메모리에 변수를 저장하여 데이터를 관리합니다. 변수 선언 방법은 크게 두 가지입니다.

### const (상수)
한 번 값을 할당하면 변경할 수 없는 상수입니다.

```tsx
const constVariable = "변경할 수 없는 상수";
console.log(constVariable);
```

### let (변수)
값을 재할당할 수 있는 변수입니다.

```tsx
let letVariable = "변경 가능한 변수";
letVariable = "새로운 값으로 변경";
console.log(letVariable);
```

### 변수 명명 규칙

```tsx
const variableRules = 
  "변수 명명 규칙\n" +
  "1. 첫 글자: 영문자, 달러($), 언더바(_)만 가능\n" +
  "2. 두 번째 글자부터: 영문자, 달러($), 언더바(_), 숫자 가능\n" +
  "3. 대소문자 구분\n" +
  "4. 예약어 사용 금지\n" +
  "5. 권장: 캐멀 케이스(camelCase)";
console.log(variableRules);
```

---

## 3. 원시 타입 변수

원시 타입은 값 자체를 저장하는 타입으로, 메모리에 직접 저장되며 복사 시 값만 복사됩니다.

### 숫자 (Number)
정수와 실수 모두 `number` 타입으로 처리됩니다.

```tsx
const integer = 100;
const float = 3.14;
console.log(typeof integer, typeof float); // number number
```

### 불리언 (Boolean)
참(`true`)과 거짓(`false`)을 나타냅니다.

```tsx
const isTrue = true;
const isFalse = false;
console.log(typeof isTrue, typeof isFalse); // boolean boolean
```

### null
의도적으로 값이 없음을 나타냅니다.

```tsx
let nullValue = null;
console.log(nullValue, typeof nullValue); // null object
// 주의: typeof null은 'object'를 반환 (JavaScript의 오래된 버그)
```

### undefined
값이 할당되지 않은 상태를 나타냅니다.

```tsx
let undefinedValue;
console.log(undefinedValue); // undefined
```

### 문자열 (String)
텍스트 데이터를 나타내며, 여러 가지 방법으로 작성할 수 있습니다.

```tsx
const str = "Hello World";
const publisher = "jpub";
const book = "typescript";

// 문자열 연결
console.log("Hello " + publisher + " " + book);

// 템플릿 리터럴 (권장)
console.log(`Hello ${publisher} ${book} ${1 + 1}`);
```

### 심벌 (Symbol)
유일한 식별자를 만들 때 사용합니다.

```tsx
const sym1 = Symbol("key");
const sym2 = Symbol("key");
console.log(sym1 === sym2); // false (각각 고유한 값)
console.log(typeof sym1);   // symbol
```

---

## 4. 참조 타입 변수

참조 타입은 메모리 주소를 저장하여 실제 데이터를 참조하는 방식입니다.

### 객체 (Object)
키-값 쌍으로 구성된 자료구조입니다.

```tsx
const myObject = {
  name: "TypeScript",
  version: "5.0"
};

// 속성 접근
console.log(myObject.name);        // 점 표기법
console.log(myObject['version']);  // 대괄호 표기법

// 속성 수정/추가
myObject.name = "JavaScript";
myObject['author'] = "Microsoft";

// 속성 삭제
delete myObject.version;
console.log(myObject);
```

#### 객체 복사의 주의점
```tsx
const obj1 = { name: "원본" };
const obj2 = obj1;  // 참조 복사
obj2.name = "변경됨";
console.log(obj1.name); // "변경됨" - 원본도 변경됨!
```

### 배열 (Array)
순서가 있는 데이터 목록입니다.

```tsx
const fruits = ["apple", "banana", "orange"];

// 인덱스로 접근 (0부터 시작)
console.log(fruits[0]);     // "apple"
console.log(fruits.at(-1)); // "orange" (마지막 요소)

// 배열 수정
fruits[1] = "grape";        // 요소 변경
fruits.push("mango");       // 끝에 추가
fruits.unshift("kiwi");     // 앞에 추가
fruits.pop();               // 마지막 요소 제거
fruits.shift();             // 첫 번째 요소 제거

console.log(fruits);
```

### 함수 (Function)
재사용 가능한 코드 블록입니다.

```tsx
// 기본 함수 선언
function greet(name: string): void {
  console.log(`안녕하세요, ${name}님!`);
}

// 반환값이 있는 함수
function add(a: number, b: number): number {
  return a + b;
}

// 함수를 변수에 할당
const multiply = function(x: number, y: number): number {
  return x * y;
};

// 화살표 함수
const divide = (x: number, y: number): number => x / y;

// 사용 예시
greet("TypeScript");
console.log(add(5, 3));      // 8
console.log(multiply(4, 2)); // 8
console.log(divide(10, 2));  // 5
```

---

## 5. 얕은 복사, 깊은 복사

### 얕은 복사 (Shallow Copy)
최상위 레벨만 복사하고, 중첩된 객체는 참조를 공유합니다.

```tsx
// 스프레드 연산자 사용
const originalObj = { name: "TypeScript", version: "5.0" };
const shallowCopy = { ...originalObj };

const originalArr = [1, 2, 3, 4];
const shallowArrCopy = [...originalArr];
```

#### 얕은 복사의 한계
```tsx
const complexObj = {
  name: "TypeScript",
  details: {
    version: "5.0",
    author: "Microsoft"
  }
};

const shallowCopy = { ...complexObj };
shallowCopy.details.version = "4.9";
console.log(complexObj.details.version); // "4.9" - 원본도 변경됨!
```

### 깊은 복사 (Deep Copy)

#### JSON 방법 (간단한 객체용)
```tsx
const deepCopy = JSON.parse(JSON.stringify(complexObj));
```

#### Lodash 사용 (권장)
```tsx
import { cloneDeep } from "lodash";

const originalObj = {
  name: "TypeScript",
  details: {
    version: "5.0",
    features: ["static typing", "interfaces"]
  }
};

const deepCopy = cloneDeep(originalObj);
deepCopy.details.version = "4.9";
console.log(originalObj.details.version); // "5.0" - 원본 유지
```

---

## 6. 조건문과 반복문

### 비교 연산자

| 연산자 | 설명 | 예시 |
|--------|------|------|
| `==` | 값 비교 (타입 변환) | `"1" == 1` → `true` |
| `===` | 값과 타입 모두 비교 | `"1" === 1` → `false` |
| `!=` | 값 불일치 | `"1" != 1` → `false` |
| `!==` | 값 또는 타입 불일치 | `"1" !== 1` → `true` |

```tsx
console.log(true == 1);   // true  (타입 변환 발생)
console.log(true === 1);  // false (타입까지 비교)
console.log("1" === 1);   // false (문자열 vs 숫자)
```

### 논리 연산자

```tsx
// AND (&&), OR (||), NOT (!)
const isLoggedIn = true;
const isAdmin = false;

console.log(isLoggedIn && isAdmin);  // false
console.log(isLoggedIn || isAdmin);  // true
console.log(!isLoggedIn);            // false

// Falsy 값들: 0, null, undefined, NaN, ""
console.log(!!0);         // false
console.log(!!"hello");   // true
console.log(!!null);      // false
```

### 조건문 (if-else)

#### 기본 사용법
```tsx
const score = 85;

if (score >= 90) {
  console.log("A학점");
} else if (score >= 80) {
  console.log("B학점");
} else if (score >= 70) {
  console.log("C학점");
} else {
  console.log("재시험");
}
```

#### 조기 반환 패턴 (권장)
```tsx
function checkUserPermission(user: any): void {
  if (!user) return console.log("사용자 정보가 필요합니다.");
  
  if (!user.id) return console.log("재로그인이 필요합니다.");
  
  if (user.roles.includes("admin")) {
    return console.log("관리자 권한입니다.");
  }
  
  if (user.roles.includes("user")) {
    return console.log("일반 사용자입니다.");
  }
}
```

### Switch 문

```tsx
const day = "Monday";

switch (day) {
  case "Monday":
    console.log("월요일");
    break;
  case "Tuesday":
    console.log("화요일");
    break;
  case "Wednesday":
    console.log("수요일");
    break;
  default:
    console.log("주말");
}
```

### 반복문

#### for 문
```tsx
// 기본 for문
for (let i = 0; i < 5; i++) {
  console.log(`반복 ${i}`);
}

// 배열 순회
const fruits = ["apple", "banana", "orange"];
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

#### forEach vs map

```tsx
const numbers = [1, 2, 3, 4, 5];

// forEach: 각 요소에 대해 작업 수행 (반환값 없음)
numbers.forEach((num, index) => {
  console.log(`${index}: ${num}`);
});

// map: 새로운 배열 생성하여 반환
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

#### while 문
```tsx
let count = 0;

while (count < 5) {
  console.log(`카운트: ${count}`);
  count++;
}

// 무한 루프 방지
let i = 0;
while (true) {
  if (i >= 3) break;
  console.log(i);
  i++;
}
```

