# Desafío: javaScript

## Nombre de Desafío: diagrama_flujo

## Instrucciones

Determiná que será impreso en la consola, sin ejecutar el código.

> Investiga cuál es la diferencia entre declarar una variable con `var` y directamente asignarle un valor.

```javascript
x = 1;
var a = 5;
var b = 10;
var c = function (a, b, c) {
  var x = 10;
  console.log(x);/* se imprime 1*/
  console.log(a);/*se imprime 5*/
  var f = function (a, b, c) {
    b = a;
    console.log(b); /*se imprime 5*/
    b = c;
    var x = 5;
  };
  f(a, b, c);
  console.log(b);/*Se imprime 5*/
};
c(8, 9, 10);
console.log(b);/*se imrpime 9*/
console.log(x);/*se imrpime 5*/
```

```javascript
console.log(bar);/*Se imprime bar*/
console.log(baz);/*Se imrpime baz*/
foo();
function foo() {
  console.log("Hola!");/*Hola*/
}
var bar = 1;
baz = 2;
```

```javascript
var instructor = "Jhoswe";
if (true) {
  var instructor = "Jose";
}
console.log(instructor);/*jhoswe*/
```

```javascript
var instructor = "Jhoswe";
console.log(instructor);/*jhoswe*/
(function () {
  if (true) {
    var instructor = "Jose";
    console.log(instructor);/*jose*/
  }
})();
console.log(instructor);/*jose*/
```

```javascript
var instructor = "Jhoswe";
let pm = "Jose";
if (true) {
  var instructor = "The Flash";
  let pm = "Reverse Flash";
  console.log(instructor);/*The Flash*/
  console.log(pm);/*Reverse Flash*/
}
console.log(instructor);/*The flash*/
console.log(pm);/*Reverse Flash*/
```

### Coerción de Datos

¿Cuál crees que será el resultado de la ejecución de estas operaciones?:

```javascript
6 / "3" /*undefined*/
"2" * "3"/*23*/
4 + 5 + "px"/*9px*/
"$" + 4 + 5 /*$9*/
"4" - 2 /*4 - 2*/
"4px" - 2 /*4px -2*/
7 / 0/*7*/
{}[0]/*0*/
parseInt("09")/*9*/
5 && 2/*52*/
2 && 5/*25*/
5 || 0/*5*/
0 || 5/*0*/
[3]+[3]-[10]/*-4*/
3>2>1/*undefined*/
[] == ![]/*undefined*/
```

> Si te quedó alguna duda repasá con [este artículo](http://javascript.info/tutorial/object-conversion).

### Hoisting

¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

```javascript
function test() {
  console.log(a);/*7*/
  console.log(foo());/*2*/

  var a = 1;
  function foo() {
    return 2;
  }
}

test();/*Se mostraran los valores que le dimos a las variables */
```

Y el de este código? :

```javascript
var snack = "Meow Mix";

function getFood(food) {
  if (food) {
    var snack = "Friskies";
    return snack;
  }
  return snack;
}

getFood(false);/*Al declarar getFood como false se va a retornar "Meow Mix"*/
```

### This

¿Cuál es el output o salida en consola luego de ejecutar esté código? Explicar por qué:

```javascript
var fullname = "Jhoswe Castro";
var obj = {
  fullname: "Jose Zuñiga",
  fullname: "Jorge Alonso",
  getFullname: function () {
    return this.fullname;
  },
};

console.log(obj.getFullname());

var test = obj.getFullname;

console.log(test()); /*Segun los strings que se definieron, el output del codigo sera devolver la cadena string en el orden en el que aparecen*/
```

### Event loop

Considerando el siguiente código, ¿Cuál sería el orden en el que se muestra por consola? ¿Por qué?

```javascript
function printing() {
  console.log(1);
  setTimeout(function () {
    console.log(2);
  }, 1000);
  setTimeout(function () {
    console.log(3);
  }, 0);
  console.log(4);
}

printing(); /*aparecera 1,3,4,2 ya que el dos tiene un setTimeout de 1000 por lo que se genera un retraso en la caneda y se imprima de ultimas */
```