# Method inlining

Одна из техник в JIT которая используется для уменьшения количества вызовов кода из других классов и методов. Например есть такой код:
```
boolean hasBoobs(String str) {
  if (str == null) {
    return false
  else
    return str.indexOf("Boobs") > 0
}

for (i in 1..1000000) {
    hasBoobs(some string...);
}
```
Видим что в цикле вызывается метод **hasBoobs()** внутри которого происходит вызов **str.indexOf()**.  Операция переходов дорогая, поэтому имеет смысл содержимое метода **str.indexOf()** скопировать прямо в тело метода **hasBoobs()**. Следующий этап - убрать метод **hasBoobs()** и вставить его содержимое в цикл.
Получается что-то вроде этого:

```
for (i in 1..1000000) {
    if (str == null) {
       return false
    else
       // тут тело метода indexOf()
}
```

Эта техника работает на уровне JIT и полностью прозрачна для программиста. При этом убираются переходы что позволяет сэкономить время и увеличить производительность.

Взято из [переписки] (https://github.com/Hexlet/hexlet-slack-archive/wiki/JIT-компиляторы.-JIT-в-JVM)

В общем виде описано [тут](http://www.oracle.com/technetwork/java/whitepaper-135217.html#method)
