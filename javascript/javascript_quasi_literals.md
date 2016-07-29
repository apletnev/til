# EcmaScript 6 Quasi-Literals

В ES6 позволяет выполнить следующие шаблоны:

```
var name = "Alex",
    msg = `Hello, ${name}!`;
console.log(msg);       // "Hello, Alex!"

var total = 30,
    msg = `The total is ${total} (${total*1.05} with tax)`;

console.log(msg);       // "The total is 30 (31.5 with tax)"
```

Такой синтаксис называется **Quasi-Literals** 

[Спецификация](http://wiki.ecmascript.org/doku.php?id=harmony:quasis)