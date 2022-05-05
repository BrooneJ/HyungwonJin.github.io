---
layout: post
title: "220430-TIL"
subtitle: "TIL-220430"
categories: til
tags: til-2022-01
comments: false
---

# Polymorphism

配列の中に色んな type の要素を入れるためには下記」のような形では実装できない

```js
type SuperPrint = {
    (arr: number[]):void
    (arr: boolean[]):void
    (arr: string[]):void
    (arr: (number|boolean)[]):void
}

const superPrint: SuperPrint = (arr) => {
    arr.forEach(i => console.log(i))
}

superPrint([1,2,3,4])
superPrint([true, false, true])
superPrint(['a','b','c'])
superPrint([1,2,true,false])
```

そこで下記のようなコードを書く必要が生じる

## Generic

call signature を作成する時、どんな type が来るか確実にわかってない時

```js
type SuperPrint = {
  <T>(arr: T[]): T,
};

const superPrint: SuperPrint = (arr) => arr[0];

const a = superPrint([1, 2, 3, 4]);
const b = superPrint([true, false, true]);
const c = superPrint(["a", "b", "c"]);
const d = superPrint([1, 2, true, false]);
```

generic を使ったら concreate type を一つ一つ書かなくてもすむ
先に<>を書いて generic を使うつもりだっていうことを宣言して書く

type をもう一個追加したい時

```js
type SuperPrint = {
  <T, M>(a: T[], b: M): T,
};

const superPrint: SuperPrint = (a) => a[0];

const a = superPrint([1, 2, 3, 4], "x");
```

# Class with TS

abstract class は直接インスタンスを作れない、ただ extends をすることができる

```js
// 継承をするだけのclass
abstract class User {
    constructor(
        protected firstName: string,
        protected lastName: string,
        protected nickName: string
    ){}
    abstract getNickname():void

    getFullName(){
        return `${this.firstName} ${this.lastName}`
    }
}

class Player extends User{
    getNickName(){
        console.log(this.nickname)
    }
}

const jin = new Player('nico', 'las', 'JIN');

// PlayerクラスはUser abstract classを継承しているため、
// getFullNameメソッドを使える
jin.getFullName()
```

# 辞書作り

```js
type Words = {
  //Propertyの名は知らないけど、typeは知っている時に
  [key: string]: string;
};
// 下記の場合はconstructorの中にwordsが入って意図したことと異なるようになる
// class Dict {
//     constructor(
//         private words: Words
//     ) {}
// }

// 結果
// class Dict{
//     constructor(words){
//         this.words = words
//     }
// }

class Dict {
  private words: Words;
  constructor() {
    this.words = {};
  }
}

class Word {
  constructor(
      public term: string,
      public def: string
    ) {}
}
```

下記は Dict に単語を登録、修正、削除する簡単な class

```js
type Words = {
  [key: string]: string
}

class Dict {
  private words:Words
  constructor(){
    this.words = {}
  }
  add(word:Word){
    if(this.words[word.term] === undefined){
      this.words[word.term] = word.def
    } else {
      console.log('It cant act add')
    }
  }
  def(term: string){
    return this.words[term]
  }
  modi(word: Word){
    if(this.words[word.term] !== undefined){
      this.words[word.term] = word.def
    } else {
      console.log('It cant act modi')
    }
  }
  del(term: string){
    if(this.words[term] !== undefined){
    //deleteを使ってオブジェクト内のプロパティを削除することができる
    // https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/delete
      delete this.words[term]
    }
  }
}

class Word{
  constructor(
    public term: string,
    public def: string
  ){}
}

const kimchi = new Word('kimchi', 'korean food')

const dict = new Dict()

dict.add(kimchi)
dict.def('kimchi')
```

# abstract class

継承するクラスがどんな動作をするか明示的に見せるため
例えば

```js
abstract class User {
    constructor(
        protected firstName: string,
        protected lastName: string
    ){}
    abstract sayHi(name:string): string
    abstract fullName():string
}
```

ここの abstract class では sayHi メソッドと fullName メソッドがどんな動作をするのか具体的に書かない
こういう引数をもらってこういう return を返すという簡略なことを書く

そして下記のようなインスタンスを作ることはできない

```js
new User();
```

# Interface

interface は軽い、abstract class は javascript で comfile した時 class として痕跡が残るが、interface は痕跡を残さなく、なくなる

```js
interface User{
    firstName:string,
    lastName:string,
    sayHi(name:string):string
    fullName():string
}

class Player implements User {
    constructor(
        //　public以外（private, protected)は利用できない
        public firstName: string,
        public lastName: string
    ){}
    fullName(){
        return `${this.firstName} ${this.lastName}`
    }
    sayHi(name:string){
        return `Hello ${name}. My name is ${this.fullName()}`
    }
}
```
