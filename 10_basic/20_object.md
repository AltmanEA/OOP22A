---
title: "Объекты"
weight: 30
---


## Объекты и ссылки

--

### Ссылка

<div class="ea_container">
	<div class="ea_column">
	<pre class="kotlin"><code>
val x = 		// Ссылка
	Array(3){it}// Функция -
				// конструктор
	</code></pre>
	</div>
	<div class="ea_column">
		<img src = "../images/object/reference.svg", width=500>
	</div>
</div>

--

### Тип объекта

<div class="ea_container">
	<div class="ea_column">
<pre class="kotlin"><code>
val s = x.size 	 // Свойство
val l = x.last()	// Функция 
	</code></pre>
	</div>
	<div class="ea_column">
		<img src = "../images/object/type.svg", width=500>
	</div>
</div>

--

### Сравнение объектов и ссылок

```Kotlin
val a = 1..5
val b = a.first.. a.last
val c = a
// Структурное равенство
println(a == b) 	 // true
println(a == c)	  // true
// Реферативное (ссылочное) равенство
println(a === b)	 // false
println(a === c) 	// true
```

--

### Сравнение вложенных объектов

```Kotlin
val t1 = arrayOf(1,2)
val a = arrayOf(t1)
val b = arrayOf(t1)
println(a == b)         // false, warning!
println(a.contentEquals(b)) 	// true

val c = arrayOf(arrayOf(1,2))
println(a == c)         // false, warning!
println(a.contentEquals(c)) 	// false
println(a.contentDeepEquals(c)) // true
```

---

## Копирование объектов

--

### Копирование примитивов и ссылок

![](../images/object/primitiveCopy1.png)

--

### Копирование примитивов и ссылок

![](../images/object/primitiveCopy2.png)

--

### Копирование объектов

![](../images/object/objectCopy0.png)

--

### Копирование объектов

![](../images/object/objectCopy1.png)

--

### Копирование массивов

![](../images/object/arrayCopy.png)

---

## Функция объектов

--

### Функция для работы с объектом

![](../images/object/last1.png)

--

### Функция объекта

![](../images/object/last2.png)

--

### Контекст объекта

![](../images/object/context.png)


--

### Лямбда функции для работы с объектами

![](../images/object/letFun.png)

---

## Свойства объектов

--

### Геттеры и сеттеры

![](../images/object/getterSetter.png)

--

### Nullable type

![](../images/object/null.png)

--

### Умное преобразование

![](../images/object/smartCast.png)
