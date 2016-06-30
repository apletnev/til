# Shadow DOM (SDOM)

SDOM - новая спецификация описывающая возможность создания элементов которые существуют не зависимо от основного DOM. В Chrome уже используется ShadowDom при использовании html5 элементов, например
```
<input type="date">
```
Если посмотреть HTML (DOM) то не увидишь компоненты календаря (span, div), однако в chrome developer tools можно включить отображение содержимого SDOM. 

Для работы с SDOM необходимо использовать метод attachShadow:

```
var element = document.getElementById('someId');
var root = element.attachShadow({mode: 'open'});
    root.appendChild(document.createElement('div'));
    root.appendChild(document.createElement('div'));
```

Не следует использовать **element.createShadowRoot()** так как он **Deprecated**

[Спецификация](http://w3c.github.io/webcomponents/spec/shadow)
[Подробнее](https://learn.javascript.ru/shadow-dom)
