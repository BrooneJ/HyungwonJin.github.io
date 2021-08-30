---
layout: post
title:  "[MySQL] Unknown database [database name]"
subtitle:   "Create MySQL"
categories: develop
tags: back mysql 
comments: true
---
## 🌟 데이터베이스 생성 시 에러
---

### 문제 발견
---
모델을 다 만들고 나서 데이터베이스를 생성하기 위해서 node app을 실행 했을 때 다음과 같이 나온다면       
![1-1](/assets/img/web/2021-08-30/1-4.png)          
<br/>

### 해결 방법
---
```
npx sequelize db:create
```
위의 명령어를 입력한다.     
<br/>

### 해결
---
![1-1](/assets/img/web/2021-08-30/1-5.png)          
위 그림과 같이      
Database react-nodebird created.        
라고 데이터베이스가 생성되었음을 알 수 있다.        