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
## mapAddPercent
---
Question    
map 메소드를 사용해 배열 각각 숫자 뒤에 %를 붙인 문자열을 만드세요    
```js
const test1 = {
  input: [100, 10, 20, 40],
  answer: ['100%', '10%', '20%', '40%'],
};
```
Answer      
```js
function solution(inputArray) {
    const mapArray = inputArray.map(el => el + '%');
    return mapArray;
}
```

## mapAppendOrder
---
Question    
배열의 값을 name 프로퍼티에 넣고 몇번째 원소인지를 order에 넣은 객체의 배열을 출력하세요    
```js
const test1 = {
  input: ['홍길동', '둘리', '루피'],
  answer: [
    { name: '홍길동', order: 1 },
    { name: '둘리', order: 2 },
    { name: '루피', order: 3 },
  ],
};
```
Answer      
```js
function solution(inputArray) {
    const answer = inputArray.map((el, idx) => {
        return {
            name: el,
            order: idx + 1
        }
    })
    return answer;
}
```

## sortByPrice
---
Question    
배열안의 객체를 price를 기준으로 오름차순 정렬한 배열을 출력하세요    
```js
const test1 = {
  input: [
    {
      name: '사과',
      price: 1000,
    },
    {
      name: '수박',
      price: 5000,
    },
    {
      name: '당근',
      price: 2000,
    },
    {
      name: '참외',
      price: 10000,
    },
  ],
  answer: [
    { name: '사과', price: 1000 },
    { name: '당근', price: 2000 },
    { name: '수박', price: 5000 },
    { name: '참외', price: 10000 },
  ],
};
```
Answer    
```js
function solution(inputArray) {
    const answer = inputArray.sort((a, b) => a.price - b.price);
    return answer;
}
```

## sortByPriceAndQuantity 
---
Question    
배열안의 객체를 price를 기준으로 오름차순 정렬한 배열을 출력하세요    
만약 price가 같다면 quantity기준으로 오름차순 정렬하세요    
```js
const test1 = {
  input: [
    {
      name: '사과',
      price: 1000,
      quantity: 2,
    },
    {
      name: '수박',
      price: 5000,
      quantity: 20,
    },
    {
      name: '당근',
      price: 2000,
      quantity: 50,
    },
    {
      name: '참외',
      price: 5000,
      quantity: 10,
    },
    {
      name: '오이',
      price: 2000,
      quantity: 49,
    },
  ],
  answer: [
    { name: '사과', price: 1000, quantity: 2 },
    { name: '오이', price: 2000, quantity: 49 },
    { name: '당근', price: 2000, quantity: 50 },
    { name: '참외', price: 5000, quantity: 10 },
    { name: '수박', price: 5000, quantity: 20 },
  ],
};
```
Answer    
```js
function solution(inputArray) {
    const answer = inputArray.sort((a, b) => {
        return a.price - b.price || a.quantity - b.quantity;
    })
    return answer;
}
```

## spreadOperatorMaxValue
---
Question    
Spread Operator를 이용해서 값의 최대, 최소값을 구하세요   
```js
const test1 = {
  input: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
  answer: 'max : 10, min : 1',
};
```
Answer      
```js
function solution(inputArray) {
    const max = Math.max(...inputArray);
    const min = Math.min(...inputArray);
    return `max : ${max}, min : ${min}`;
}
```

## reduceNameNickname
---
Question      
입력받은 객채배열의 nickname을 key, name을 value로 하는 객체를 출력하세요     
```js
[
    {
      name: '홍길동',
      nickname: 'hong',
    },
    {
      name: '둘리',
      nickname: '2li',
    },
    {
      name: '오스트랄로피테쿠스',
      nickname: '1Cin',
    },
  ],
  answer: { hong: '홍길동', '2li': '둘리', '1Cin': '오스트랄로피테쿠스' },
};
```
Answer      
```js
function solution(inputArray) {
    const answer = inputArray.reduce((prev, current) => {
        return {
            ...prev,
            [current.nickname]: current.name,
        }
    }, {});
    return answer;
}
```

## reduceMaxValueNIndex
---
Question    
reduce 메소드를 사용해 최댓값의 값을 maxValue에, 해당 값의 index를 idx에 넣은 객체를 출력하세요   
```js
const test1 = {
  input: [3, 29, 38, 12, 57, 74, 40, 85, 61],
  answer: { maxValue: 85, idx: 7 },
};

const test2 = {
  input: [-24, -2, -13, -49, -999999, -17],
  answer: { maxValue: -2, idx: 1 },
};
//최댓값이 중복일 때에는 먼저 나온 최댓값의 인덱스를 유지하도록 설정하였습니다.
const test3 = {
  input: [2, -20, 21, -874, 99, -16, -29, 99],
  answer: { maxValue: 99, idx: 4 },
};
```
Answer    
```js
function solution(inputArray) {
    const answer = inputArray.reduce((acc, cur, idx) => {
        if (acc?.maxValue < cur) {
            return {
                maxValue: cur,
                idx,
            }
        }
        return acc;
    }, { maxValue: -1e9, idx: -1 })
    return answer;
}
```

## expDivOdd
---
Question    
제곱한 후 3으로 나눈 나머지가 홀수인 것 을 뽑은 배열의 총 합을 구하세요.    
```js
const test1 = {
  input: [1, 7, 3, 4, 6],
  answer: 66,
};

const test2 = {
  input: [2, 3, 6, 8, 10],
  answer: 168,
};
```
Answer      
```js
function solution(inputArray) {
    const answer = inputArray.reduce((acc, cur) => {
        if ((cur ** 2) % 3 === 1) {
            return acc + cur ** 2;
        }
        return acc;
    }, 0)
    return answer;
}
```