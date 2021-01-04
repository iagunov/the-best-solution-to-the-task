# **The best solution to the task**

Здесь собраны мои наиболее удачные решения задач, которые возможно будут полезны.


## **Pallindrom**

Задача: проверить, является ли слово паллиндромом, то есть его перевернутый вид должен быть идентичен изначальному, выдать true усли это так и false если нет.

```
const palindrom = str => str == str.toLowerCase().split('').reverse().join('');
```

Здесь мы используем стрелочную функцию и оператор строгого сравнения, где слева исходная строка, а справа мы приводим все символы к нижнему регистру, после этого преобразуем строку в массив строк, после этого с помощью метода ```reverse``` переворачиваем строку, после этого сново объединяем символы с помощью метода ```join```, результат сравнения и есть наш ответ. 
P.S. Очень люблю решения в одну строку :)

## **Unique array values**

Задача: оставить в массиве только уникальные значения и вывести их в новом массиве.

```
const unikFunc = Array.from(new Set(unik));
```

Здесь мы используем структуру данных ```Set``` которая хранит только уникальные значения массива, далее с помощью метода ```Array.from()``` преобразуем структуру данных в массив.

## **Comparing two arrays**

Задача: сравнить два массива, если они равны, выдать true, если не равны false, если хоть один аргумент не является массивом, выдать что это не массив.__(Массивы не содержат элементы которые сами являются массивами, так же игнорируется присвоение по ссылке(задача в посимвольном сравнении, то что массивы равны только если они присвоены по одной и той же ссылке игнорируется))__

```
function arrIdentical (a, b) {
  if (!(Array.isArray(a) || Array.isArray(b))) return "this is not an array";
  
  let i = a.length;
  
  if (i != b.length) return false;
  while (i--) {
    if (a[i] !== b[i]) return false;
  }
  return true;
}
```

Здесь с помощь метода ```Array.isArray()``` мы определяем, являетются ли оба аргумента массивами, если хоть один не являтеся, выдаем "this is not an array". Позже мы сравниваем длины масивов с помощью метода ```length```, если длины не равны, значит и массивы не равны, выдаем false. Далее с помощью цикла ```while``` мы сравниваем элементы массивов посимвольно, если все символы строго равны, значит массивы равны.

## **Number to digit tiers**

Задача: создать функцию, которая принимает число и возвращает массив строк, содержащих число, отрезанное на каждой цифре, пример:

2017 должен вернуться ["2", "20", "201", "2017"]

```
function createArrayOfTiers(num) {
    let result = '';
    return [...num + ''].map(value => {
      return result += value;
    });
};
```

Здесь мы сначала заводим счетчик result и присваиваем ему пустую строку. Далее мы разворачиваем аргумент num в массиве с помощью оператора ```spread``` (оператор ```spread``` развернутый в квадратных скобках приводит строку к массиву строк), но здесь аргумент число, поэтому, мы прибавляем к аргументу пустую строку что бы привести его к строке и получаем массив строк. Далее с помощью метода ```map``` мы итерируем каждое значение массива и прибавляем его к счетчику(сложение строк) и результат каждой итерации это новое значение нового массива.

## **Is the number divisible by 3**

Задача: дана строка из положительного целого числа и нужно определить, делится оно на 3 или нет.

```
let divisibleByThree = (str) => (str.split('').map(parseFloat).reduce((a, b) => a + b)) % 3 ? false : true;
```
Здесь сначала с помощью метода ```split``` мы приводим строку к массиву строк, после методом ```map(parseFloat)``` мы приводим каждое значение к числу, после мы суммируем все значения с помощью метода ```reduce``` и после мы проверяем, делится оно на 3 без остатка или нет, если остаток есть, значит не делится, выдаем false, если остатка нет то true.

## **Сhanging a line**

Задача: дана строка, в строке некоторые гласные заменены цифрами (a=0, e=1, i=2, o=3, u=4), так же посреди строки есть два слова trex и raptor, их необходимо не учитывать, нужно расшифровать строку и написать ее с загдавной буквы, кроме того, если в строке встречается I (в значении "я"), ее необходимо написать с большой буквы, если i это часть слова (например "Dinosaurs"), то необходимо оставить ее маленькой, в конце предложения должна быть точка.

```
function nonsense(str) {
  let resStr = str.toLowerCase()
              .replace(/0|1|2|3|4/g, e => 'aeiou'[e])
              .replace(/trex|raptor/g, '')
              .replace(/^.| i /g, s => s.toUpperCase()) + (str.slice(-1) === '.' ? '' : '.');
  
  return resStr[0].toUpperCase() + resStr.substring(1);
}
```
Сначала мы приводим все символы к нижнему регистру с помощью метода ```toLowerCase```, далее открытие недели(я в восторге от этого метода), методом ```replace``` заменяем сначала цифры на символы, после слова trex|raptor на пустую строку и после если перед I ничего нет, то с помощью метда ```toUpperCase``` приводим к верхнему регистру, далее, с помощью метода ```slice``` с флагом -1 прибавляем точку если ее нет, и если она есть то ничего не прибавляем. Далее в новой переменной мы приводим первый символ к верхнему регистру(отсчет начинается с 0), далее прибавляем оставшуюся строку начиная со второго символа(индекс 1) с помощью метода ```substring```.




