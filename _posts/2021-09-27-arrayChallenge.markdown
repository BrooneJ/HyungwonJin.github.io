---
layout: post
title:  "[ArrayChallenge] array challenge"
subtitle:   "filter forEach"
categories: algorithm
tags: programmers
comments: true
---

## everyArray
---
Question)        
every를 이용해서 모든 원소가 짝수인지 아닌지를 판별하세요       
```js
const test1 = {
  input: [2, 4, 6, 8, 10],
  answer: true,
};

const test2 = {
  input: [2, 3, 6, 8, 10],
  answer: false,
};
```
Answer)      
```js
function solution(inputArray) {
    return inputArray.every((idx) => idx % 2 === 0);
}
```

## filterAge
---
Question)
배열 원소의 age가 30이상 50미만인 사람만 있는 객체의 배열을 만드세요        
```js
const test1 = {
  input: [
    {
      name: '영미',
      age: 25,
    },
    {
      name: '일미',
      age: 35,
    },
    {
      name: '이미',
      age: 45,
    },
    {
      name: '삼미',
      age: 55,
    },
  ],
  answer: [
    { name: '일미', age: 35 },
    { name: '이미', age: 45 },
  ],
};
```
Answer
```js
function solution(inputArray) {
    const result = inputArray.filter((input) => input.age >= 30 && input.age < 50);
    return result;
}
```

## filterOdd 
---
Question        
홀수만 뽑아 배열로 만드세요
```js
const test1 = {
  input: [4, 2, 5, 1, 3],
  answer: [5, 1, 3],
};

const test2 = {
  input: [4, 2, 6, 8, 50, 16],
  answer: [],
};

const test3 = {
  input: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11],
  answer: [1, 3, 5, 7, 9, 11],
};
```
Answer          
```js
function solution(inputArray) {
    const result = inputArray.filter(el => el % 2 === 1);
    return result;
}
```

## forEachFilter
---
Question            
배열 원소중 40 이상인 수만 뽑아 배열을 만드세요.        
```js
const test1 = {
  input: [100, 10, 20, 40],
  answer: [100, 40],
};
```
Answer      
```js
function solution(inputArray) {
    const result = inputArray.filter((el) => el >= 40);
    return result;
}
```

## forEachFilterIsNaN
---
Question
배열 원소중 숫자인 원소만 뽑아 배열을 만드세요.     
```js
const test1 = {
  input: [1, 40, '라매', '개발자', 51.5, 'a', 88],
  answer: [1, 40, 51.5, 88],
};

const test2 = {
  input: [1, 2, 3, '4', 5, '6'],
  answer: [1, 2, 3, 5],
};

const test3 = {
  input: [-3, -2, -1, 0, 1, 2, 3],
  answer: [-3, -2, -1, 0, 1, 2, 3],
};
```
Answer      
```js
function solution(inputArray) {
    const array = [];
    inputArray.forEach(el => {
        if (typeof el === 'number') {
            array.push(el);
        }
    })
    return array;
}
```

## findWord
---
Question        
용가리라는 단어가 있으면 true 없으면 false를 출력       
```js
const test1 = {
  input: ['잠', '자', '고', '싶', '다', '용가리'],
  answer: true,
};
const test2 = {
  input: ['맛있는', '용가리치킨'],
  answer: false,
};
const test3 = {
  input: ['고질라', '용가리 ', '울트라맨'],
  answer: false,
};
```
Answer      
내 풀이
```js
function solution(inputArray) {
    const array = [];
    inputArray.forEach(el => {
        if (el === '용가리') {
            array.push(el);
        }
    })
    if (array.length !== 0) {
        return true
    }
    return false
}
```
다른 사람 풀이      
```js
function solution(inputArray) {
    let answer = false;
    inputArray.find(el => {
        if (el === '용가리') {
            answer = true;
        }
    })
    return answer
}
```

## forEachMap
---
Question        
forEach 메소드를 사용해서 배열의 각 원소 끝에 '%'를 붙인 문자열 배열을 출력하세요       
```js
const test1 = {
  input: [100, 10, 20, 40],
  answer: ['100%', '10%', '20%', '40%'],
};
```
Answer      
```js
function solution(inputArray) {
    const array = [];
    inputArray.forEach(el => {
        array.push(el + "%");
    })
    return array;
}
```

## forEachReduce
---
Question        
forEach 메소드를 사용해서 배열의 총 합을 출력하는 코드를 작성하세요     
```js
const test1 = {
  input: [100, 10, 20, 40],
  answer: 170,
};

const test2 = {
  input: [120, -20, -30, 0, 15],
  answer: 85,
};

const test3 = {
  input: [-10, -20, -30],
  answer: -60,
};
```
Answer      
```js
function solution(inputArray) {
    const reducer = (prev, current) => prev + current;
    const answer = inputArray.reduce(reducer);
    return answer;
}
```
```js
let sum = 0;
inputArray.forEach((el) => {
  sum += el;
})
```