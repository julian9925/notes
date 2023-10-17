---
id: 675b8kkz5z5exjtsavxig5r
title: classConstructor
desc: ''
updated: 1697447867473
created: 1697447546622
---

# Javascript class do what

預期這段會執行什麼？

```javascript
let f = function () {
  this.a = 1;
  this.b = 2;
};

let proto1 = f();
console.log(proto1.a);
```

new 做了什麼事情

* **創建一個新的物件**：new 運算符創建一個全新的、空的 JavaScript 物件 {} 實體。
* **設定原型**：新物件的 Prototype（一個隱藏的內部屬性）被設定為物件的原型屬性。換句話說，新物件從建構函數的原型中繼承。
* **執行建構函數**：帶有指定參數的建構函數（例如 new f() 中的 f）被調用，並將 this 設定為新創建的物件。這一步是物件初始化的地方，可以添加屬性，附加方法等等。
* **返回創建的物件**：如果建構函數沒有顯式地返回一個物件（return { /*...*/ }），那麼由 new 創建的新物件將自動被返回。然而，如果建構函數確實返回一個物件，則將返回該物件，而不是新創建的物件。

``` javascript
let f = function () {
  this.a = 1;
  this.b = 2;
};

let proto1 = f();
console.log(proto1.prototype);

let proto1 = new f();
console.log(proto1.__proto__);

console.log(proto1.getPrototypeOf(proto1));

console.log(Object.getPrototypeOf(proto1));
```

物件本身沒有 prototype 屬性，只有函數有 prototype

在 JavaScript 中實現了「第一類函數」（First-Class Function）的特性，這意味著函數可以作為參數傳遞給其他函數，可以從其他函數返回，也可以被賦值給變量，或者作為物件的屬性。函數還有一些其他的特性，比如擁有一個 prototype 屬性（只有函數才有這個屬性），可以被用作建構函數來創建新的物件

在 JavaScript 中，函數也是物件，所以 Object 事實上就是一個特殊的函數，可以用來創建新的物件或者返回已經存在的物件的參考。由於 Object 是一個函數，它自然地擁有 prototype 屬性。這個 prototype 屬性是一個物件，包含了所有由 Object 建構函數創建的物件所繼承的屬性和方法，如 Object.prototype.hasOwnProperty、Object.prototype.toString 等。

最安全的繼承方法

```
let SuperClass = function() {
    this.a = 1;
    this.b = 2;
}

let SubClass = function() {
    superClass.call(this);
}

SubClass.prototype = Object.create(SuperClass.prototype);
SubClass.prototype.constructor = SubClass;

```


![](/assets/prototype_chain.drawio.png)

#javascript