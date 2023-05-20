---
title: "Классы"
weight: 40
---

# Понятие класса

--

### Простой класс

```Kotlin
class Student(
    val firstname: String,
    val surname: String
){
    fun getFullName() = "$firstname $surname"
}
```

```Kotlin
val ivan: Student = Student("Иван", "Иванов")
outputConsole.print(ivan.firstname)
outputConsole.print(ivan.getFullName())
```

--

### Свойства класса

```Kotlin
class Student(
    val firstname: String,
    val surname: String
){
    val fullName = "$firstname $surname"
}
```

```Kotlin
val ivan = Student("Иван", "Иванов")
outputConsole.print(ivan.firstname)
outputConsole.print(ivan.fullName)
```

--

### Параметры конструктора

```Kotlin
class Student(
    firstname: String,
    surname: String = ""
){
    val fullName = "$firstname $surname"
}
```

```Kotlin
val ivan = Student("Иван", "Иванов")
// outputConsole.print(ivan.firstname) !
outputConsole.print(ivan.fullName)
```

--

### Функции и операторы

```Kotlin
operator fun String.unaryPlus(): String {
    outputConsole.print("$this\n")
    return this
}

class Student(
    val firstname: String,
    val surname: String
)

fun main() {
    val ivan = Student("Иван", "Иванов")
    val i = 1
    +"$i - $ivan" // toString() fun
}
```
```Kotlin
1 - lec1.Student@4dd8dc3
```

---

# Конструкторы

--

### Вторичный конструктор

```Kotlin
class Student(
    val firstname: String,
    val surname: String
){
    constructor(fullName: String): this(
        fullName.split(" ")[0],
        fullName.split(" ")[1]
    )
    val fullName
        get() = "$firstname $surname"
}
```

--

### Блок инициализации

```Kotlin
class Student(
    fullName: String
){
    val firstname: String
    val surname: String

    init {
        val nameList = fullName.split(" ")
        firstname = nameList[0]
        surname = nameList[1]
    }
}
```

--

### Порядок инициализации

```Kotlin
class Student(
    val name: String = +"Параметр конструктора"
) {
    val a: String = +"Объявление свойства"
    init {
        val b = +"Блок инициализации"
    }
    val c: String = +"Объявление 2 свойства"
}

```
```
Параметр конструктора
Объявление свойства
Блок инициализации
Объявление 2 свойства
```

---

# Дополнительные возможности классов


--

### Свойства объекта компаньона

```Kotlin
class Student(
    val name: String = +"Создаю $default"
) {
    companion object {
        var default = +"По умолчанию"
    }
}
fun main() {
    +"Начало программы"
    Student.default = +"Иван Иванов"
    val ivan = Student()
    Student.default = +"Петр Петров"
    val petr = Student()
    // ivan.default - нет поля
}
```
```
Начало программы
По умолчанию
Иван Иванов
Создаю Иван Иванов
Петр Петров
Создаю Петр Петров
```

--

### Функции объекта компаньона

```Kotlin
class Student(val name: String = +"Создаю $default") {
    companion object {
        var default = +"Иван Иванов"
        fun updateDefault(update:(String)->String){
            default = update(default)
        } } }
fun main() {
    +"Начало программы"
    Student.updateDefault {
        it.replace("Иван ", "Петр ")
    }
    +"Создаю студента"
    val petr = Student() }
```
```
Начало программы
Иван Иванов
Создаю студента
Создаю Петр Иванов
```

--

### Модификаторы видимости

```Kotlin
companion object {
	var default: String = +"Иван Иванов"
    	private set(value) {
			field = value
        }
    fun updateDefault(update:(String)->String){
    	default = update(default)
    }
}
// main
+"Начало программы"
// Student.default = "Петр Иванов" !
Student.updateDefault { it.replace("Иван ", "Петр ")}
```

```
public
private
protected
```


---

# Дополнительные виды классов

--

### Синглтон

```Kotlin
object Univer{
    val name: String = +"Университет"
}

fun main() {
    +"Начало программы"
    +"Использую ${Univer.name}"
}
```

```
Начало программы
Университет
Использую Университет
```

--

### Перечисление

```Kotlin
enum class WeekType { ODD, EVEN }

enum class ClassType(val shortname: String){
    Лекция("лек")
}

fun main() {
    val x = WeekType.ODD
    +"${x.name}"
    val y = ClassType.Лекция
    +"$y, ${y.shortname}"
}
```

```
ODD
Лекция, лек
```

--

### Классы данных

```Kotlin
data class Student(
    val firstname: String,
    val surname: String
)

fun main() {
    val ivan = Student("Иван", "Иванов")
    +"$ivan"    					// toString() fun
    val petr = ivan.copy(firstname = "Петр")
    val (pf, ps) = petr 			// componentX() fun
    +"${Student(+pf, +ps)==petr}"   // equals() fun
}
```

```
Student(firstname=Иван, surname=Иванов)
Петр
Иванов
true
```
