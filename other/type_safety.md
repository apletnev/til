# Type safety (Типобезопасность)

Термин указывающий на то, что прежде чем выполняются операции над переменными проводится проверка их типов. Проверка производится либо во время компилирования либо во время выполнения программы.
Например type safe позволяет предотвратить следующие операции в Java:

```
String one = 1; //error
int foo = "bar"; //the same

int AddTwoNumbers(int a, int b) {
    return a + b;
}
int Sum = AddTwoNumbers(5, "5"); //error
```

Пример из **JavaScript** который не является type safe языком:
```
AddTwoNumbers: function(var a, var b) {
    return a + b;
}
console.log(AddTwoNumbers(5, “5”)); //will return “55” as string 
```

