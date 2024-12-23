Регулярные выражения (Regular Expressions или RegEx) в JavaScript — это мощный инструмент для работы с текстом. Они позволяют искать, заменять, проверять и извлекать текстовые данные на основе заданных шаблонов.

---

## **1. Что такое регулярное выражение**

**Регулярное выражение** — это шаблон, который используется для сопоставления строк или их частей.  
В JavaScript регулярные выражения создаются двумя способами:

1. **С использованием литералов**:
    
    ```javascript
    const regex = /pattern/flags;
    ```
    
2. **С использованием конструктора**:
    
    ```javascript
    const regex = new RegExp('pattern', 'flags');
    ```
    

---

## **2. Флаги регулярных выражений**

Флаги изменяют поведение регулярного выражения:

|Флаг|Описание|
|---|---|
|`g`|Глобальный поиск (поиск всех совпадений)|
|`i`|Игнорирование регистра|
|`m`|Многострочный поиск|
|`s`|Позволяет символу `.` находить символы новой строки|
|`u`|Включает поддержку Юникода|
|`y`|"Скользящий" поиск (начиная с текущей позиции)|

### **Пример использования флагов:**

```javascript
const regex = /hello/i; // Игнорирование регистра
console.log(regex.test('Hello')); // true
```

---

## **3. Методы работы с регулярными выражениями**

### **1. Методы строки**

1. **`str.match()`**  
    Ищет совпадения с шаблоном. Возвращает массив совпадений или `null`.
    
    ```javascript
    const result = 'Hello, world!'.match(/hello/i);
    console.log(result[0]); // 'Hello'
    ```
    
2. **`str.matchAll()`**  
    Возвращает итератор для всех совпадений (поддерживает группы).
    
    ```javascript
    const matches = 'a1b2c3'.matchAll(/\d/g);
    for (const match of matches) {
        console.log(match[0]); // 1, 2, 3
    }
    ```
    
3. **`str.search()`**  
    Возвращает индекс первого совпадения или `-1`.
    
    ```javascript
    const index = 'Hello, world!'.search(/world/);
    console.log(index); // 7
    ```
    
4. **`str.replace()`**  
    Заменяет совпадения на указанную строку.
    
    ```javascript
    const replaced = 'abc'.replace(/a/, 'x');
    console.log(replaced); // 'xbc'
    ```
    
5. **`str.split()`**  
    Разбивает строку на массив по указанному шаблону.
    
    ```javascript
    const parts = 'a,b,c'.split(/,/);
    console.log(parts); // ['a', 'b', 'c']
    ```
    

---

### **2. Методы объекта RegExp**

1. **`regex.test()`**  
    Проверяет, соответствует ли строка шаблону. Возвращает `true` или `false`.
    
    ```javascript
    const regex = /\d+/;
    console.log(regex.test('123')); // true
    console.log(regex.test('abc')); // false
    ```
    
2. **`regex.exec()`**  
    Ищет совпадение. Возвращает массив с информацией о первом совпадении или `null`.
    
    ```javascript
    const regex = /(\d+)/;
    const match = regex.exec('abc123');
    console.log(match[0]); // '123'
    console.log(match[1]); // '123' (группа)
    console.log(match.index); // 3 (позиция в строке)
    ```
    

---

## **4. Синтаксис регулярных выражений**

### **1. Символы**

|Символ|Описание|
|---|---|
|`.`|Любой символ, кроме новой строки|
|`\d`|Цифра (0-9)|
|`\D`|Не цифра|
|`\w`|Буква, цифра или `_`|
|`\W`|Не буква, не цифра, не `_`|
|`\s`|Пробельный символ|
|`\S`|Не пробельный символ|
|`\b`|Граница слова|
|`\B`|Не граница слова|

#### **Пример**

```javascript
const regex = /\d+/;
console.log('abc123xyz'.match(regex)); // ['123']
```

---

### **2. Квантификаторы**

|Символ|Описание|
|---|---|
|`*`|0 или более|
|`+`|1 или более|
|`?`|0 или 1|
|`{n}`|Ровно `n` раз|
|`{n,}`|`n` или более|
|`{n,m}`|От `n` до `m` раз|

#### **Пример**

```javascript
const regex = /\d{2,4}/;
console.log('12345'.match(regex)); // ['1234']
```

---

### **3. Группы**

1. **Скобки `()`**  
    Используются для создания групп.
    
    ```javascript
    const regex = /(abc)+/;
    console.log('abcabc'.match(regex)); // ['abcabc', 'abc']
    ```
    
2. **Незахватывающая группа `(?:...)`**  
    Не сохраняет совпадение.
    
    ```javascript
    const regex = /(?:abc)+/;
    console.log('abcabc'.match(regex)); // ['abcabc']
    ```
    
3. **Ссылки на группы**  
    Ссылка на предыдущую группу: `\1`, `\2` и т.д.
    
    ```javascript
    const regex = /(\w+)\s\1/;
    console.log('hello hello'.match(regex)); // ['hello hello', 'hello']
    ```
    

---

### **4. Символьные классы**

- `[abc]` — Любой из символов `a`, `b`, `c`.
- `[^abc]` — Любой символ, кроме `a`, `b`, `c`.
- `[a-z]` — Диапазон символов.

---

### **5. Якоря**

|Символ|Описание|
|---|---|
|`^`|Начало строки|
|`$`|Конец строки|

#### **Пример**

```javascript
const regex = /^hello$/;
console.log(regex.test('hello')); // true
console.log(regex.test('hello world')); // false
```

---

## **5. Практическое использование**

### **Проверка формата данных**

1. **Электронная почта:**
    
    ```javascript
    const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    console.log(emailRegex.test('test@example.com')); // true
    ```
    
2. **Номер телефона:**
    
    ```javascript
    const phoneRegex = /^\+?[0-9]{10,15}$/;
    console.log(phoneRegex.test('+1234567890')); // true
    ```
    
3. **Проверка URL:**
    
    ```javascript
    const urlRegex = /^(https?:\/\/)?([\w.-]+)\.([a-z]{2,6}\.?)(\/[\w]*)*\/?$/;
    console.log(urlRegex.test('https://example.com')); // true
    ```
    

---

## **6. Лучшая практика**

1. **Используйте флаги `g` и `i`, если это необходимо.**
2. **Оборачивайте шаблоны в скобки для ясности.**
3. **Для сложных выражений используйте комментарии (в библиотеке XRegExp).**
4. **Тестируйте регулярные выражения на онлайн-сервисах, например, [regex101](https://regex101.com/).**