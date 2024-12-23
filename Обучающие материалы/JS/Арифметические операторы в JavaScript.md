JavaScript поддерживает широкий набор математических операций и функций. Вот основные моменты, которые стоит знать.

---

### 1. **Базовые арифметические операции**

|Операция|Синтаксис|Пример|Результат|
|---|---|---|---|
|Сложение|`+`|`5 + 3`|`8`|
|Вычитание|`-`|`10 - 4`|`6`|
|Умножение|`*`|`7 * 2`|`14`|
|Деление|`/`|`9 / 3`|`3`|
|Остаток от деления|`%`|`10 % 3`|`1`|
|Возведение в степень|`**`|`2 ** 3`|`8`|

---

### 2. **Особенности операций**

#### **Оператор сложения `+`**

- Работает как **арифметический оператор** для чисел.
- Работает как **оператор конкатенации** для строк.
    
    ```javascript
    console.log(5 + 3);       // 8
    console.log("Hello " + "World!"); // "Hello World!"
    console.log("5" + 3);     // "53" (строка)
    ```
    

#### **Оператор остатка `%`**

Используется для получения остатка от деления.

```javascript
console.log(10 % 3); // 1
console.log(8 % 2);  // 0
```

#### **Возведение в степень `**`

Возводит число в указанную степень.

```javascript
console.log(2 ** 3); // 8
console.log(4 ** 0.5); // 2 (квадратный корень)
```

---

### 3. **Инкремент и декремент**

|Операция|Синтаксис|Пример|Результат|
|---|---|---|---|
|Инкремент|`++`|`x++` или `++x`|Увеличивает на 1|
|Декремент|`--`|`x--` или `--x`|Уменьшает на 1|

- **Постфиксная форма** (`x++` или `x--`): Возвращает значение до изменения.
- **Префиксная форма** (`++x` или `--x`): Возвращает значение после изменения.

```javascript
let x = 5;
console.log(x++); // 5 (сначала возвращает, потом увеличивает)
console.log(x);   // 6

let y = 5;
console.log(++y); // 6 (сначала увеличивает, потом возвращает)
```

---

### 4. **Операторы присваивания**

|Оператор|Синтаксис|Эквивалент|
|---|---|---|
|Присваивание|`=`|`x = y`|
|Сложение и присваивание|`+=`|`x += y` => `x = x + y`|
|Вычитание и присваивание|`-=`|`x -= y` => `x = x - y`|
|Умножение и присваивание|`*=`|`x *= y` => `x = x * y`|
|Деление и присваивание|`/=`|`x /= y` => `x = x / y`|
|Остаток и присваивание|`%=`|`x %= y` => `x = x % y`|
|Возведение в степень и присваивание|`**=`|`x **= y` => `x = x ** y`|

```javascript
let a = 5;
a += 3; // a = a + 3
console.log(a); // 8
```

---

### 5. **Порядок выполнения операций (Приоритет)**

При выполнении выражений JavaScript следует определённому порядку:

1. **()** Скобки.
2. **`**`** Возведение в степень.
3. **`*`**, **`/`**, **`%`** Умножение, деление и остаток от деления.
4. **`+`**, **`-`** Сложение и вычитание.

```javascript
console.log(2 + 3 * 4); // 14 (умножение выполняется первым)
console.log((2 + 3) * 4); // 20 (скобки имеют высший приоритет)
```

---

### 6. **Специальные значения**

#### **`NaN` (Not-a-Number)**

Возникает, если результат математической операции не является числом.

```javascript
console.log("abc" * 2); // NaN
console.log(typeof NaN); // "number"
```

#### **`Infinity` и `-Infinity`**

Возникают при делении числа на `0` или слишком больших результатах.

```javascript
console.log(1 / 0); // Infinity
console.log(-1 / 0); // -Infinity
```

---

### 7. **Математические функции (Math)**

#### **Основные методы Math:**

- **`Math.round(x)`**: Округляет до ближайшего целого.
- **`Math.ceil(x)`**: Округляет вверх.
- **`Math.floor(x)`**: Округляет вниз.
- **`Math.trunc(x)`**: Убирает дробную часть.
- **`Math.sqrt(x)`**: Возвращает квадратный корень.
- **`Math.pow(x, y)`**: Возводит число `x` в степень `y`.
- **`Math.abs(x)`**: Возвращает модуль числа.
- **`Math.max(a, b, ...)`**: Возвращает максимальное значение.
- **`Math.min(a, b, ...)`**: Возвращает минимальное значение.
- **`Math.random()`**: Возвращает случайное число от `0` до `1`.

#### Примеры:

```javascript
console.log(Math.round(4.5)); // 5
console.log(Math.ceil(4.2));  // 5
console.log(Math.floor(4.8)); // 4
console.log(Math.sqrt(16));   // 4
console.log(Math.pow(2, 3));  // 8
console.log(Math.abs(-10));   // 10
console.log(Math.max(5, 3, 8)); // 8
console.log(Math.random());   // Случайное число от 0 до 1
```

---

### 8. **Преобразование типов в математических операциях**

- При математических операциях строки, содержащие числа, автоматически преобразуются в тип `number`.
- Если строка не содержит числа, результат будет `NaN`.

```javascript
console.log("5" * 2); // 10
console.log("5" - 1); // 4
console.log("abc" + 2); // "abc2" (конкатенация)
console.log("abc" * 2); // NaN
```

---

### 9. **Работа с остатком и делением**

- Остаток от деления можно использовать для проверки чётности числа:

```javascript
let number = 10;
if (number % 2 === 0) {
    console.log("Число чётное");
} else {
    console.log("Число нечётное");
}
```

---

### Полезные примеры:

1. **Генерация случайного числа от 1 до 100:**

```javascript
let randomNumber = Math.floor(Math.random() * 100) + 1;
console.log(randomNumber);
```

2. **Возведение в степень:**

```javascript
console.log(2 ** 10); // 1024
console.log(Math.pow(2, 10)); // Тоже 1024
```

3. **Округление числа до 2 знаков после запятой:**

```javascript
let num = 12.34567;
console.log(Math.round(num * 100) / 100); // 12.35
```