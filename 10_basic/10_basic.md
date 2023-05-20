# Переменные и константы

~-~

### Объявления переменных

```Kotlin
val a: Int = 1	// Общий вид
val b = 2		 // Тип `Int` выводится компилятором
val c: Int		// Без инициализации тип обязателен
c = 3			 // Отложенная инициализация
var x = 5		 // Тип `Int` выводится компилятором
x += 1			// var можно изменять
```

~-~

### Целочисленные типы и константы

```Byte``` (8 бит),
```Short``` (16),
```Int``` (32),
```Long``` (64).

```Kotlin
val one = 1 // Int
val threeBillion = 3000000000 // Long
val oneLong = 1L // Long
val oneByte: Byte = 1

val hex = 0x0F
val bin = 0b00001011

val oneMillion = 1_000_000
```

~-~


### Вещественные типы и константы

```Float``` (32, IEEE754 single),

```Double``` (64, IEEE754 double).

```Kotlin
val pi = 3.14 // Double
// val one: Double = 1 // Error: type mismatch
val oneDouble = 1.0 // Double
val e = 2.7182818284 // Double
val eFloat = 2.7182818284f // Float, actual value is 2.7182817

val scienceNotation = 123.5e10
```

~-~

### Символьные типы и константы

```Char``` (1 символ, поддерживает Unicode),

```String``` (Строка).

```Kotlin
val aChar: Char = 'a'
println(aChar)
println('\n')
println('\uFF00')

val s = "Hello, world!\n"
val text = """
    for (c in "foo")
        print(c)
"""
```

~-~

### Логический тип и константы

```Boolean```

```Kotlin
val myTrue: Boolean = true
val myFalse: Boolean = false
```

~--~

# Операции 

~-~

### Арифметические 

| prefix | postfix | infix | assignment |
|--------|---------|-------|------------|
| +a     | a++     | a+b   | a+=b       |
| -a     | a--     | a-b   | a-=b       |
| ++a    |         | a*b   | a*=b       |
| --a    |         | a/b   | a/=b       |
|        |         | a%b   | a%=b       |

~-~

### Побитовые

- shl(bits)  – signed shift left
- shr(bits)  – signed shift right
- ushr(bits)  – unsigned shift right
- and(bits)  – bitwise and
- or(bits)  – bitwise or
- xor(bits)  – bitwise xor
- inv()  – bitwise inversion

~-~

### Логические

- ||  – логическое ИЛИ (ленивое)
- &&  – логическое И (ленивое)
- !  - negation

Ленивые операции:
```Kotlin
if (b != 0 && a/b > 2)
 ...
```

~-~

### Сравнение

- a == b
- a != b
- a < b
- a > b
- a <= b
- a >= b

---

# Сложные типы данных

~-~

### Примитивы и объекты

```Kotlin
val number: Int = 1
val numberString: String = number.toString()
```

- Объекты имеют больше возможностей.
- Примитивы требуют меньше ресурсов.
- Kotlin автоматически выбирает представление встроенных типов.

~-~

### Массивы

```Kotlin
val x: IntArray = intArrayOf(1, 2, 3) 	// массив примитивов
val y: Array< Int > = arrayOf(1, 2, 3)	// массив объектов
// Первый аргумент Array - размер массива
// второй - функция инициализации (i - индекс элемента)
val z: Array< Int > = Array(5, { i -> i*i }) 

x[0] = у.size		  // 3
x[1] = z.last()		// 16
```

~-~

### Коллекции

```Kotlin
val x = ArrayList<Int>()
x.addAll(listOf(1, 2, 3))
x.add(5)
print(x)
```
```
[1, 2, 3, 5]
```

~-~

### Структуры данных

```Kotlin
class Good(val price: Float, val name: String)

val mail: Good = Good(10F, "mail")
val awl: Good = Good(20F, "awl")

val total = mail.price + awl.price
```

~-~

### Диапазоны

```Kotlin
val r1: IntRange = 1..10
val r2: IntProgression = 10 downTo 1 step 2

println(5 in r1)
println(5 !in r2)
```
```
true
true
```

~-~

### Строки. Представление.

```Kotlin
val i = 42
val s = "answer is $i"
val charArray: CharArray = s.toCharArray()
charArray[0] = charArray[0].uppercaseChar()
val newS: String = String(charArray)
print(newS)
```
```
Answer is 42
```

~-~

### Строки. Операции.

```Kotlin
val s1 = "string one"
println(s1.uppercase())
println(s1.replace(" ", "_"))
println(s1.substring(1 .. 3))
println(s1.split(" "))
```
```
STRING ONE
string_one
tri
[string, one]
```

~-~

### Кортежи (tuples)

```Kotlin
val p: Pair<Int, String> = Pair(1,"")
val t: Triple<Int, String, Char> = 
        Triple(p.first, p.second, '1')
```

~--~

# Управляющие конструкции

~-~

### Ветвление

```Kotlin
if (a % 2 == 0)
	print("a is even\n")
else
	print("a is odd\n")

val min = if (a < b) a else b
```

- Условие имеет тип Boolean.
- Возвращает значение.

~-~

### Выбор

```Kotlin
var result = when(a){
	in 0..6 -> "ночь"
	in 6..12 -> "утро"
	in 12..18 -> "день"
	in 18..24 -> "вечер"
	else -> "ошибка"
}
```
- Структурная конструкция (нет break!).

~-~

### Цикл для перебора

```Kotlin
for(i in 0..5){
    print(i)
}
```
```Kotlin
val a = arrayOf(1, 2, 3)
var s = 0
for(x in a){
	s += x
}
```
- Применяется при заранее известном числе повторений.

~-~

### Цикл для итерации

```Kotlin
var bits = 10
while (bits > 0) {
    val tmp = bits / 2
    print(bits - 2 * tmp)
    bits = tmp
}
```
```Kotlin
print("\nEnter Yes\n")
do {
    val x = readLine()
} while (x != "Yes")
```

~-~

### Прерывание циклов

Kotlin содержит операторы ```continue```(завершить шаг цикла) и ```break``` (завершить цикл), но при правильном подходе к реализации алгоритмов они не нужны.

---

# Функции

~-~

### Объявление и вызов

```Kotlin
fun greeting(name: String): String {
    return "Hello $name"
}

print(greeting("Sheldon"))
```

~-~

### Аргументы по умолчанию

```Kotlin
fun greeting(name: String,
            prefix: String = "Dr."): String {
    return "Hello $prefix $name\n"
}

print(greeting("Sheldon"))
print(greeting("Howard", "Mr"))
```

~-~

### Именнованные аргументы

```Kotlin
fun greeting(name: String,
            prefix: String = "Dr.",
            greeting: String = "Hello"): String {
    return "Hello $prefix $name\n"
}

print(greeting("Sheldon", greeting = "Hi"))
```

~-~

### Функции из одного выражения

```Kotlin
fun greeting(name: String,
            prefix: String = "Dr.",
            greeting: String = "Hello") =
    "Hello $prefix $name\n"
```

~-~

### Лямбда-функции

```Kotlin
val arr: Array< Int > = Array(10) { it }

val isEven: (Int) -> Boolean = { n: Int -> n.rem(2) == 0 }

val evenArr: Array< Boolean > = Array(10, isEven)

val sum: (Int, Int) -> Int = { x: Int, y: Int -> x + y}
```
