# Dead Code Elimination (DCE)

Один из подходов используемый в  JIT и в классических компиляторах. Например необходимо проверить выход за границы массива. 
```
int[] array = ….
int bounds = paramFromRuntime();
for (i = 0; i < bounds; i++) {
   doSomething(array[i]);
}
```
JIT определяет что переменная **bounds** точно меньше размера массива. Поэтому выбрасываются все проверки чтобы бросить exception **ArrayIndexOutOfBoundsException**

Если размер bounds меньше массива то из бинарника выбросится все лишнее и будет что-то вроде этого:
```
for (i in 0 …. bounds) {
   val item = array[i]
}
```

если переменная больше массива, то код будет следующим:
```
for (i in 0 …. bounds) {
   if (i < 0 || i > array.size)
      throw ArrayIndexOutOfBoundsException()
   else
      val item = array[i]
}
```

Если цикл в цикле и циклом погоняет, то подобная оптимизация влияет на производительность кода.

Взято из [переписки] (https://github.com/Hexlet/hexlet-slack-archive/wiki/JIT-компиляторы.-JIT-в-JVM)