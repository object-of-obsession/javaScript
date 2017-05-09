## Learn JavaScript

- [Типы данных](#Типы-данных)
- [Строки](#Строки)
- [Числа](#Числа)
- [Массивы](#Массивы)
- [Методы массивов](#Методы-массивов)
- [Объекты](#Объекты)
- [Прототипы объектов](#Прототипы-объектов)
- [Циклы](#Циклы)
- [Функции](#Функции)
- [Стрелочные функции](#Стрелочные-функции)
- [Сallback](#callback)
- [Классы](#Классы)
- [DOM](#DOM)
- [Замыкание](#Замыкание)
- [Get/Set](#getset)
- [Обработчики события](#Обработчики-события)
- [Объект событий](#Объект-событий)
- [this - контекст исполнения функции](#this---контекст-исполнения-функции)
- [Декораторы](#Декораторы)





## Типы данных
```javascript
// Простые типы данных
var myNumber = 2525
    myString = "Somestring"
    myBool = true
    myNull = null
    myUndef = undefined

// Объектные типы
var obj = {name: "sorax"}
    array = [1, 2, 3]
    regexp = /w+/g
    func = function(){}
```
## Строки
### Получаем длину строки
```javascript
var string = "terrible";
string.lenght; // 8

'42'.length;   // 2
```


### Экранирование запрещенных символов
```javascript
'it's my life';
'ist\'s my life';
```


### Строки vs. символы

в JS нет типа данных для символа. Символ это строка с одним символом.
```javascript
'abcdef'.charAt(2);    // 'c'
'abcdef'.charAt(200); // ''
'abcdef'.charAt(-1);  // ''
```


### Конкатенация
```javascript
'abcdef'.charAt(0) + 'abcdef'.charAt(2) + 'abcdef'.charAt(4); // 'ace' 

'together' + 'again'; // 'together again'

12 + 'or' + '20'; // '12 or 20' (при склеивании числа и строки мы получаем строку)
```


### Строки и числа
```javascript
12 + ' or ' + '20'; // '12 or 20' (в этом примере чило 12 интерпретируется как строка и на выходе мы получаем строку)

'12' / 2 + 1 // 7; (при математической операции не сложение, а например делении происходит обратная ситуация. Тут 12 интерпретируется как число и мы получаем число на выходе)

'day' * 2; // NaN 
```

### Перевод числа в строку. Для этого истользуется оператор toString();
```javascript
var a = 42; // 42
a.toString(); // '42'
a.toString().lenght; // 2 (так как длина это число мы получаем строку)
a.toString().length.toString(); // '2' (и теперь обратно переводим это число в строку)
```

### Работа со скобками
```javascript
'Blink ' + 182 // 'Blink 182' (так есть строка, у нас все склеивается и мы получаем строку)

'Blink ' + 182 + 1 // 'Blink 1811' (ситуация аналогичная, не смотря на то, что у нас два числа. Все равно все склеится, так как у нас есть строка)

'Blink ' + (181 + 1) // 'Blink 182' (тут мы получим нужный результат, так как мы выводим математическую операцию "сложение" в скобки. На выходе мы получаем склеивание строки с результатом замкнутой математической операции)
```

### Сравнение строк (как не странно, но строки стравниваются в алфавитном порядке. Это касется не только единичных символов, но и целых строк. В них сравнение идет посимвольно)
```javascript
'a' < 'b'; // true
'c' < 'b'; // false

'abcd' < 'abcd'; // false (мы получим false, так как на самом деле строки равны)
'abcd' < 'abdc'; // true (а тут получим true третий символ и первой строки больше)


'toy' === 't' + 'o' + 'y' // true (конкатиницию строк JavaScript интерпритирует как строку поэтому мы получим true)
```
## Числа 
### Ошибочные числа

1/0 = infinity
-1/0 = - infinity
NaN = не числовые значения

1. Любая операция с NaN дает NaN
2. NaN != NaN
3. isNaN(...)



### Преобразование
```javascript
var y = 43.81327
y.toFixed(); // '44'
y.toFixed(1); // 43.8
y.toFixed(2); // 43.1

var n = 7432
n.toString(); // '7432'
```
## Массивы
* Объект напоминает список, который обладает некоторыми методами и свойствами.

* Ни размер, ни тип элементов массива не фиксированы.

* "Длинна" массива не является верхней гранцей

(Это значит, что водном масиве мы можем хранить числа одновременно со строками, объектами, null, undefined итд)

### Рекоммендуемый способ
```javascript
var myArray = [];
var cities = ['Moscow', 'Almaty', 'Kiev', 'New York'];
```

### Создание с помощью конструктора функфии Array
```javascript
var a = newArray();
var b = newArray('Hey', 'You', 'Me');
var c = newArray(3);
```

### Length
* Length - это индекс последнего элемента + 1
* Значение length можно изменять

Не совсем логичное поведение.
Допустим у нас есть массив
```javascript
var a = ['a', 'b', 'c'];
a.length; // 3

a[0] // 'a'
a[1] // 'b'
a[2] // 'c'
a[3] // undefined
```

Затем мы добавляем элемент с индексом 10
```javascript
a[10] = 'what?'
```

И длина нашего массива становится равной 11 (индекс последнего элемента + 1) не смотря на то, что у нас 
образовалось пропасть между элементами с индексами 2 и 10
```javascript
a.lenght; // 11
```


### Удаление

* delete
* splice
```javascript
массив[1].delete // удалит элемент с индексом 2
```
```javascript
массив.splice(3, 1); // откуданачать, сколько удалить
```


### Перебор элементов массива
```javascript
for(var i=0; i < a.lenght; i++) {
  // выведет все элементы массива
}
```
## Методы массивов
* reduce /* сумма всех элементов массива */
* concat /* конкатенация массивов */
* push/pop /* чуть более удобный способ удаления/добавления элементов массива */
* join /* разделитель между элементов массива */
* reverse /* данный метод изменяет исходный массив. После его применения порядок элементов в массиве меняется на обратный */
* sort /* сортировка */


## Объекты

* Объект - контейнер со свойствами;
* Все - объекты (кроме чисел, строк, true/false - переменных, null и undefined);
* Функция - объект, массив - объект, объект - обект.


### Пример объекта
```javascript
var obj = {};

var person = {
	'name' : 'Alex',
	'age' : 25
}
```

### Обращение
```javascript
persone.name; // 'Alex'
persone.age; // 25
```

Идентификатор свойства может быть указан без ковычек, но если идентификатор свойства пустая строка, тогда нам необходимо поставить ковычки.

### Пример объекта
```javascript
var person = {
	name : 'Alex',
	age : 25
	'' : 'WEIRD!'
}
```
### Обращение (можно обращаться через квадратные скобочки)
```javascript
a['name']; // 'Alex'
a['age']; // 25
a[''];	// 'WEIRD!'
```


Названия индентификаторов объектов не всегда нужно оборачивать в ковычки, за исключением тех случаев, когда в названиях используются спецсимволы.
```javascript
var person = {
	name : 'Alex', // ок
	bad-thing : 22, // ошибка
	'good-thing' : 23, // ок
	':;;:' : 24 // ок
};
```


### Вложенность 

Значение свойства может содержать число, строку, но также ничего не мешает ему содержать другой объект.
```javascript
var persone = {
	name : 'Alex',
	wife : {
		name : 'Eve',	
		age : 29;
	}
	age : 25
};
```



### Обращение к вложенным данным
```javascript
person.wife; // Object
person.wife.age; // 29
person.wife.wife // undefined
```


### Обновление
```javascript
var person = {
	name : 'Alex',
	age : 25
}

person.height; // undefined (так как нет свойства height)

person.name = 'Peter'; (перезаписываем значение)
persone.height = 178; (добавляем свойство)

person.name; // 'Peter'
person.height; // 178
```


## Прототипы объектов 
Объекты в JavaScript можно организовать в цепочки так, чтобы свойство, не найденное в одном объекте, автоматически искалось бы в другом.

Связующим звеном выступает специальное свойство __proto__.

### Прототип proto

```javascript
Если один объект имеет специальную ссылку __proto__ на другой объект, то при чтении свойства из него, если свойство отсутствует в самом объекте, оно ищется в объекте __proto__.

Свойство __proto__ доступно во всех браузерах, кроме IE10-, а в более старых IE оно, конечно же, тоже есть, но напрямую к нему не обратиться, требуются чуть более сложные способы, которые мы рассмотрим позднее.

var e = {
  eat: 'fish'
}

function Animal(name) {
  this.name = name;
  this.__proto__ = e; 
}

var bear = new Animal('bear');
console.log(bear.eat); / fish
```

## Циклы 

### For

for (инициализация; тест; инкремент) {
  тело цикла
}
  
```javascript
for (i = 1; i < 10; i++) {
  console.log(i)
}
```

```javascript
for (i = 1=; i--) {
  console.log(i)
}
```

### While

```javascript
while (выражения) {
  инструкция
}
```

```javascript
var i = 10;
while(i--) {
  console.log(i)
}
```

### Do While

```javascript
do 
  инструкция; 
while 
  (выражение)
```

```javascript
  do 
    console.log(i);
  while
    (i < 10);
```


## Функции
Функция - это объект

* Со свойствами name, lenght и prototype;
* Может использоваться как любой другой объект: храниться в переменных, других объектах (Если функция находится внутри объекта, то мы называем эту функцию методом), передаваться как аргумент, возврящаться как значение;
* Функция можно задавать свойства и методы;
* В отличии от других объектов функцию можно вызвать.

### Общий вид функции
```javascript
зарезервированное_слово имя_функции(параметры) {
  тело функции // параметры внутри в теле функции являются переменными
}
```
### Анонимная функция
имя_функции - необязательно, если его нет то такую функцию мы называем анонимной.


## Стрелочные функции
Стрелка должна идти сразу после параметров, если спустить ее на строку ниже, то получим ошибку

### Функция с двумя параметрами
```javascript
/* Старый синтаксис */
function add(x, y){
	return x + y;
}

/* Новый синтаксис */
let add =(x, y) => x + y;
```


### Функция с одним параметром
Если функция принимает только один параметр, то нет необхоимости его заключать в круглые скобки
```javascript
/* Старый синтаксис */
let square = function(x){
	return x * x;
}

/* Новый синтаксис */
let square = x => return x * x;
```


### Функция, которая вообще не принимает параметров
```javascript
/* Старый синтаксис */
let givMeAnswer = function(){
	return 42;
}

/* Новый синтаксис */
let givMeAnswer = () => return 42;
```

### Функция, которая не возвращает ничего
```javascript
/* Старый синтаксис */
let log = function(){
	console.log('Logging');
}

/* Новый синтаксис */
let log = () => console.log('Logging');
```

### Функция, тело которой состоит из двух строк
Если в теле функции несколько строк, мы должны использовать фигурные скобки и также  мы должны указать что функция возвращает.
```javascript
/* Старый синтаксис */
let multuply = function(x, y){
	var result = x * y;
	return result;
}

/* Новый синтаксис */
let multuply = (x, y) => {
	var result = x * y;
	return result;
}
```


### Функция, которая возвращает литерал объекта
Если функция возвращает литерал объекта, то нам нужно обернуть его в круглые скобки
```javascript
/* Старый синтаксис */
let getPersone = function(x, y){
	return { name : 'John' };
}

/* Новый синтаксис */
let getPersone = (x, y) => ({ name : 'John' });
```

### Функция, которая вызывается и тут же возвращается (IIFE)
IIFE - Immediately Invoked Function Expression

```javascript
/* Старый синтаксис */
(function(){
	console.log('IIFE');
})();

/* Новый синтаксис */
(() => console.log('IIFE'))();
```


/* Написать про практическое применение стрелочных функций с Массивами */


## Callback
### Что такое функция callback

Это функция которую запустят позднее. Как пример callback-а можно привести обычный обработчик события.

Коллбэки нужны что-бы вы могли запустить функцию не прямо сейчас, а чтобы другая функция могла запустить ее позже. Например браузер может запустить функцию после того как выпонится событие (например клик). Либо вы сами можете запустить функцию, когда что-то произойдет.

Как пример функция вопрос. Допустим я хочу спросить пользователя о чем-ниубудь. И в случае если он скажет свое имя мне нужно сделать какое-то одно действие (например doSomething). Иначече другое действие (handleError).

Зачем это может понадобиться? Предстатвьте вам нужно 20 раз спросить имя человека вы же не будете 20 раз писать promt. 
Если он не ввел значение вам нужно 20 раз обработать это как ошибку вы же не будете 20 раз ставить if.

Для этого вы делаете функцию, функцию Ask.

https://yadi.sk/i/ZNS6HDNr3EFgS3


## Классы

Свои классы на прототипах. Используем ту же структуру, что JavaScript использует внутри себя, для объявления своих классов.

### Обычный конструктор

Вспомним, как мы объявляли классы ранее.

Например, этот код задаёт класс Animal в функциональном стиле, без всяких прототипов:

```javascript
function Animal(name) {
  this.speed = 0;
  this.name = name;

  this.run = function(speed) {
    this.speed += speed;
    alert( this.name + ' бежит, скорость ' + this.speed );
  };

  this.stop = function() {
    this.speed = 0;
    alert( this.name + ' стоит' );
  };
};

var animal = new Animal('Зверь');

alert( animal.speed ); // 0, начальная скорость
animal.run(3); // Зверь бежит, скорость 3
animal.run(10); // Зверь бежит, скорость 13
animal.stop(); // Зверь стоит
```

### Класс через прототип

А теперь создадим аналогичный класс, используя прототипы, наподобие того, как сделаны классы Object, Date и остальные.

Чтобы объявить свой класс, нужно:

Объявить функцию-конструктор. Записать методы и свойства, нужные всем объектам класса, в prototype.
Опишем класс Animal:

```javascript
// конструктор
function Animal(name) {
  this.name = name;
  this.speed = 0;
}

// методы в прототипе
Animal.prototype.run = function(speed) {
  this.speed += speed;
  alert( this.name + ' бежит, скорость ' + this.speed );
};

Animal.prototype.stop = function() {
  this.speed = 0;
  alert( this.name + ' стоит' );
};

var animal = new Animal('Зверь');

alert( animal.speed ); // 0, свойство взято из прототипа
animal.run(5); // Зверь бежит, скорость 5
animal.run(5); // Зверь бежит, скорость 10
animal.stop(); // Зверь стоит
```

В объекте animal будут храниться свойства конкретного экземпляра: name и speed, а общие методы – в прототипе.

Совершенно такой же подход, как и для встроенных классов в JavaScript.


## Замыкание
Это идея в программировании очень старая и очень мощная и это одна из тех вещей, которая в JavaScript сделана хорошо.

Если мы в функции используем переменную находящуюся в глобальном объекте, то мы не можем гарантировать, что ничего не взорвется. К примеру туда может быть подключена либа, в которой переменные называются также и тогда будет конфликт.

Мы создаем переменную каждый раз когда вызывем функцию

```javascript
var getAnswer = fucnction(){
	var answer = 42;
	return answer;
};
```

/* Но если мы делаем замыкание, то мы имеем доступ к */

Мы создаем переменную getAnswer и задаем значение этой переменной тому что вернет внутренняя функция. Внутрення функция имеет доступ к тому что находится вне ее. И на самом деле мы обращаемся к answer в тот момент когда его уже не существует. Так как мы jбращамся после того, как она завершила свою работу. Тем не менее мы имеем доступ к тому что было внутри функции в момент запуска - это и есть замыкание.

```javascript
var getAnswer = (function() {
	var answer = 42;

	return function inner(){
		returm answer;
	};
}());
```

## DOM

### Дерево DOM
DOM нужен для того, чтобы манипулировать странице. Дом это объектная модель документа. Любой узел является объектом и через JavaScript мы можем изменять его свойства

```javascript
document.body.backgroundColor = 'red'
```
Через JavaScript можно динамически создавать новые элементы, добавлять их на страницу, удалять их со странице итд.
```javascript
document.documentElement // Соответствует тегу html
```
```javascript
document.body // Соответствует тегу body
```

Получив ссылку на элелемент, можно побродить по его потомкам.
```javascript
document.body.firstChild
```

```javascript
document.body.firstNodes[0]
```

```javascript
document.body.firstChild.nextSibling
```

```javascript
document.body.firstChild.nextSibling.nextSibling
```

Мотод для получения всех дочерних узлов исключая пробел. Children это псевдомассив, который содержит все узлы и элементы.
```javascript
document.body.children
```

Помимо универсальных навигационнах ссылок есть дополнительние. Например для форм, для таблиц.
```javascript
 table.rows[0].cells[1]
 ```
 
Свойство которое показывает тип узла. Сущетвует всего 12 типов узлов (узел элемент 1, текстовый узел 3).
```javascript
document.body.nodeType
```
Свойтво, которое показывает имя узла (всегда большими буквами).
```javascript
document.body.nodeName
```

Свойство содержимого. C помошью него можно как получить содержимое, так присвоить (это свойство есть только у узлов элементов, у текстовых узлов его нет).
```javascript
document.body.innerHTML
```

Для текстовых узлов используется свойство data, оно так же позволяет получать и менять содержимое.
```javascript
document.body.firstChild.data // предположим что это текст
```
### Аттрибуты и пользовательские свойства
Методы для работы с аттрибутами.
```javascript
getAttribute(name)
setAttribute(name, value)
hasAttribute(name)
removeAttribute(name)
attributes(name) // коллекция котора все аттрибуты
```

```javascript
ol.getAttribute('data-description') // <ol data-description="Свойства и методы для работы с атрибутами">
```
Получается, что с одной стороны у DOM элементов есть свой свойтва, как у обычных элементов с другой стороны есть атрибуты, которые можно устанавливать с помощью методов.


### Методы поиска
```javascript
document.getElementById(id)
document.getElementByName(name)
document.evaluate(xpath)
elem.getElementByTagName(tag)
elem.getElementByClassName(className)
elem.querySelectorAll(css)
elem.querySelector(css) // Современный способ
```



## Get/Set
```javascript
class GetThings {
  constructor(size) {
    this.length = size;
  }
  
  get Length() {
    return this.length;
  }
  
  set Lenght(value) {
    this.length = value;
    console.log('Значение установленно');
  }  
}

/*
var thing = new GetThings(9);
thing.Length;
thing.Length = 10;
https://www.youtube.com/watch?v=nx6DFeNIXlA
*/
```

## Обработчики события
### Обработка событий через атрибут (быстрый способ на коленке)

```html
<ul>
	<li onclick="alert('привет')"></li>
</ul>
```

### Обработка событий через свойство (хоть сколько-нибудь масштабируемый код, позволяет поставить обработчик только одного типа на элемент)

```javascript
var li = document.querySelector('li'); //получаем ссылку на элементы
li.onclick = function(){ // и ставим ему свойство
  alert('привет')l
}
```

### Современные методы назначения обработчиков, позволяет поставить несколько обработчиков на одно событие
Он получает имя сообытия например клик, функцию обработчик, третий аргумент который обычно равен false.

```javascript
var li = document.querySelector('li');

function sayHi(){
  alert('Привет!');
}

function sayHi2(){
  alert('Привет, еще раз!');
}

li.addEventListener('click', sayHi, false);
li.addEventListener('click', sayHi, false);
```


### Удаление обработчика
Для того чтобы удалить обработчик его сначало нужно куда-нибудь записать.
```javascript
var f = function sayHi(){
  alert('Привет');
}

li.addEventListener('click', f, false);
li.removeEventListener('click', f, false);
```


В обработчике события this это текущий элемент на котором сработал обработчик, доступ к нему можно получить следующим образом.
```javascript
var f = function sayHi(){
  alert(this);
}

li.addEventListener('click', f, false);
```
## Объект событий 
Для того чтобы обработать событие нам мало знать на каком элементе оно произошло, могут понадобиться дополнительные детали произошедшего и они находятся в специальном объекте event. Он передается первым аргументам в функцию обработчик событий. У него очень много свойств. Он содержит как свойства вообще любых событий:
- Например свойство event.type (тип события)
- Например свойство event.target (элемент на котором произошло собыитие)

Так и свойства, которые есть только у событий мыши. Например свойство:
- Например свойство clientX: 57
- Например свойство clientY: 81

Однако у браузеров есть рассинхрон относительно свойств событий. Поэтому для работы с событиями лучше воспользоваться фреймворком, даже если вы предпочитаете работать на чистом JavaScript



## this - контекст исполнения функции 

### this Default Binding
** this будет ссылаться на Lexical scoupe в котором вызывается функция (в данном случае глобальный объект). **
```javascript
function foo() {
  console.log(this.a);
}

var a = 2;

foo();
```


### this Implicit Binding (скрытое связывание)
** this будет указывать на объект из которого вызывается функция. **
```javascript
function foo() {
  console.log(this.a);
}

var obj = {
  a: 2,
  foo: foo
}

obj.foo;
```


### this Explicin Binding (явное связывание)
** Явно задачем объект (c помощью call или apply) на который будет указывать this. **
```javascript
function foo() {
  console.log(this.a);
}

var a = 'global';

var obj = {
  a: 2
}

foo.call( obj ) //2
foo.apply( obj ) //2
```

Чтобы указать контекст выполнения любой функций вы можете использовать три метода: call, apply и bind. При использовании первых двух методов происходит вызов функции “на месте”, метод bind функцию не вызывает, вместо этого он возвращает новую функцию с заданным контекстом.


/* Тут написать пример для bind */


/* Тут написать пример для стрелочных функций. У стрелочных функций свое поведение */




### this New Binding (связывание при создание объекта через конструктор)
** Как работает конструктор:**
- На лету создается новый объект;
- Этот объект становится контекстом исполнения данной функции (именно в даный момент);
- Функция автоматически вернет это объект, даже если мы ничего не будем возвращать.

```javascript
function foo() {
  this.a = a;
}

var bar = new foo(2);

console.log( bar.a ); //2
```


## Декораторы
Декоратор позволяет мощно и гибко модифицировать поведение функции (обертка, которая модифицирует поведение функции).

Декоратор это функция, она получает другую функцию и какие-то параметры. Ее задача это вернуть обертку вокруг функции.
Это обертка иногда что-то делает потом возвращает функцию (и потом может опять что-то делает с результатом).

```javascript
// decorator(f, ...) = обертка вокруг f
```

Смысл обертки это модифицировать поведение f при этом синтаксис вызова как правило остается таким же

```javascript

function doubleDqecorator(f) {
	return function(){
		return 2*f.apply(this, arguments); /* f.apply(this, arguments) передаем все аргументы, которые получила обертка */
	}
}

function sum(a + b) {
	return a + b;
}

sum = doubleDecorator(sum);

alert( sum(1,2) ); //6
```
