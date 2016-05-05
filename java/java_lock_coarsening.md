# Lock coarsening (Укрупнение блокировок)

Подход заключается в поиске системных блокировок (lock, synchronized, mutex) и объединение их.

Например есть функции: 
```
void someFunc() {
   mutex();
  //some code
   mutex();
}

void mutex() {
   get_mutex() //syscall
   value++
   release_mutex()
}
```

Так как вызов mutex очень дорогой (вызывается системная функция), то JIT производит укрупнение блокировок. В результате функция будет вот такой:

```
void mutex() {
   get_mutex()
   value++
   value++
   release_mutex()
}
```

В результате вызов функции **get_mutex()** уменьшили вдвое, однако кода в блокировке стало больше, поэтому и называется метод **“Укрупнение блокировок”**

Взято из [переписки] (https://github.com/Hexlet/hexlet-slack-archive/wiki/JIT-компиляторы.-JIT-в-JVM)

Более подробное описание [тут](http://www.ibm.com/developerworks/library/j-jtp10185/index.html)