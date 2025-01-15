# JavaScript 구조 분해 할당 (Destructuring Assignment) 정리

JavaScript의 **구조 분해 할당(Destructuring Assignment)** 은 배열이나 객체의 값을 쉽게 추출하여 변수에 할당할 수 있는 문법입니다. ES6(ECMAScript 2015)에서 도입된 이 기능은 코드를 간결하고 가독성 있게 작성하는 데 매우 유용합니다.

---

## 📖 구조 분해 할당이란?

- **구조 분해 할당**은 배열과 객체의 내부 구조를 분해하여 개별 변수에 값을 할당하는 문법입니다.
- 배열은 **순서(index)** 를 기준으로, 객체는 **키(key)** 를 기준으로 값을 추출합니다.

---

## 📂 배열 구조 분해 (Array Destructuring)

### **1. 기본 사용법**
- 배열의 각 요소를 변수에 순서대로 할당합니다.
```
const numbers = [1, 2, 3];
const [a, b, c] = numbers;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
```

---

### **2. 기본값 설정**
- 배열 요소가 없는 경우 기본값을 설정할 수 있습니다.
```
const numbers = ;
const [x = 1, y = 2] = numbers;

console.log(x); // 10
console.log(y); // 2 (기본값 사용)
```

---

### **3. 나머지 요소 추출 (Rest 연산자)**
- `...`를 사용하여 나머지 요소를 별도의 배열로 추출할 수 있습니다.
```
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;

console.log(first); // 1
console.log(second); // 2
console.log(rest); // [3, 4, 5]
```

---

### **4. 값 교환**
- 구조 분해를 이용하면 두 변수의 값을 간단히 교환할 수 있습니다.
```
let a = 1;
let b = 2;

[a, b] = [b, a];

console.log(a); // 2
console.log(b); // 1
```

---

## 📂 객체 구조 분해 (Object Destructuring)

### **1. 기본 사용법**
- 객체의 키(key)를 기준으로 값을 추출하여 변수에 할당합니다.
```
const user = { name: "Alice", age: 25 };
const { name, age } = user;

console.log(name); // "Alice"
console.log(age); // 25
```

---

### **2. 변수 이름 변경**
- 객체의 키와 다른 이름의 변수를 사용할 수 있습니다.
```
const user = { name: "Alice", age: 25 };
const { name: userName, age: userAge } = user;

console.log(userName); // "Alice"
console.log(userAge); // 25
```

---

### **3. 기본값 설정**
- 객체에 해당 키가 없을 경우 기본값을 설정할 수 있습니다.
```
const user = { name: "Alice" };
const { name, age = 18 } = user;

console.log(name); // "Alice"
console.log(age); // 18 (기본값 사용)
```

---

### **4. 나머지 속성 추출 (Rest 연산자)**
- `...`를 사용하여 나머지 속성을 별도의 객체로 추출할 수 있습니다.
```
const user = { name: "Alice", age: 25, city: "Wonderland" };
const { name, ...rest } = user;

console.log(name); // "Alice"
console.log(rest); // { age: 25, city: "Wonderland" }
```

---

## 📂 중첩 구조 분해

### **1. 중첩된 객체**
- 중첩된 객체의 값을 추출할 때도 구조 분해를 사용할 수 있습니다.
```
const user = {
    name: "Alice",
    address: {
        city: "Wonderland",
        zip: "12345"
    }
};

const { address: { city, zip } } = user;

console.log(city); // "Wonderland"
console.log(zip); // "12345"
```

---

### **2. 중첩된 배열**
- 중첩된 배열에서도 구조 분해가 가능합니다.
```
const numbers = [1, [2, 3], 4];
const [a, [b, c], d] = numbers;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
console.log(d); // 4
```

---

## 📂 함수 매개변수에서의 구조 분해

### **1. 함수 인자에서 배열 구조 분해**
- 함수 매개변수로 전달된 배열을 직접 구조 분해할 수 있습니다.
```
function sum([a, b]) {
    return a + b;
}

console.log(sum([10, 20])); // 30
```

---

### **2. 함수 인자에서 객체 구조 분해**
- 함수 매개변수로 전달된 객체를 직접 구조 분해할 수 있습니다.
```
function greet({ name, age }) {
    console.log(`Hello ${name}, you are ${age} years old.`);
}

greet({ name: "Alice", age: 25 }); 
// 출력: Hello Alice, you are 25 years old.
```

#### 기본값 설정:
```
function greet({ name = "Guest", age = 18 }) {
    console.log(`Hello ${name}, you are ${age} years old.`);
}

greet({}); 
// 출력: Hello Guest, you are 18 years old.
```

---

## 🛠️ 활용 사례

### 데이터 처리:
구조 분해는 API 응답 데이터를 처리하거나 복잡한 데이터 구조에서 필요한 값만 추출하는 데 유용합니다.
```
// API 응답 예시:
const response = {
    data: {
        id: 123,
        title: "JavaScript Basics",
        author: {
            name: "John Doe",
            email: "john@example.com"
        }
    }
};

const { data: { title, author: { name } } } = response;
console.log(title); // "JavaScript Basics"
console.log(name);   // "John Doe"
```

---

## ✨ 요약

1. **배열 구조 분해**:
   - 순서를 기준으로 값을 추출하며 기본값 설정 및 나머지 요소 추출이 가능.

2. **객체 구조 분해**:
   - 키(key)를 기준으로 값을 추출하며 변수 이름 변경 및 기본값 설정이 가능.

3. **중첩된 데이터**:
   - 중첩된 객체나 배열에서도 구조 분해를 활용 가능.

4. **함수 매개변수**:
   - 함수 인자에서 직접 구조 분해를 사용하여 데이터를 처리.

---
