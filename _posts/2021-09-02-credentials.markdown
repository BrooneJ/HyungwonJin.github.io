---
layout: post
title:  "[TroubleShooting] front-back) Credentials 설정 문제"
subtitle:   "saga"
categories: develop
tags: front
comments: true
---

# Credentials 설정 문제

## 🚔 문제 발견 
---
![1-1](/assets/img/web/2021-09-02/1-1.png)          
브라우저는 3000번 포트, 백엔드는 3065 포트를 사용하고 있다. 따라서 현재는 도메인이 다르기 때문에 cookie가 전달되지 않고 있어 백엔드에서는 post를 누가 보낸 것인지 알 방법이 없다.       
그래서 현재 로그인하고 있음에도 불구라고 401 Unauthorized라는 메세지를 받게 되었다.     

## 🔍 해결 방법
---
1. proxy로 해결하는 방법
2. cors로 해결하는 방법     

여기서는 cors로 해결하는 방법을 사용한다.       
🗂 back/app.js
```javascript
app.use(cors({
    origin: '*', // Access-controll-allow-origin
->  credentials: true, // Access-controll-allow-credentials
}));
```
🗂 sagas/post.js        
```javascript
function addPostAPI(data) { // 제네레이터 아님
    return axios.post('/post', { content: data }, {
        withCredentials: true,
    });
}
```
withCredentials를 true로 해주면 쿠키도 같이 전송된다.

<br/>

또는 

🗂 sagas/index.js
```javascript
axios.defaults.withCredentials = true;
```
위와 같은 코드를 입력해두면 모든 API에 직접 입력할 필요가 없어진다.     
<br/>

하지만 이렇게하면 두번째 문제가 발생하게 된다.      
![1-1](/assets/img/web/2021-09-02/1-2.png)          

이는 withCredentials를 true로 해줬기 때문에 일어나는 문제이다.      
보안을 철저하게 하기 위해서 orgin에 아무나 허용되지 않게 정확한 주소를 적어달라는 것이다. 

🗂 sagas/app.js
```javascript
app.use(cors({
    origin: '*',
    credentials: true,
}));
```

## ✅ 해결
---
![1-1](/assets/img/web/2021-09-02/1-3.png)          
위의 그림과 같이 status의 상태가 200번 대로 바뀌는 것을 볼 수 있다.     