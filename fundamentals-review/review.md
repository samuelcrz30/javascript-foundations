# Repaso de fundamentos de JavaScript

## Constructor `String` y método `toString()`

- **Definición**: Un objeto string se utiliza para representar una secuencia de caracteres. Los objetos string se crean utilizando la función constructora `String`, que envuelve el valor primitivo en un objeto.

```js
const greetingObject = new String("Hello, world!");

console.log(typeof greetingObject); // "object"
```

- **Método `toString()`**: Este método convierte un valor a su representación en forma de cadena de texto. Es un método que puedes utilizar con números, booleanos, arrays y objetos.

```js
const num = 10;
console.log(num.toString()); // "10"

const arr = [1, 2, 3];
console.log(arr.toString()); // "1,2,3"
```

Este método acepta una base opcional (`radix`), que es un número del 2 al 36. Esta base representa la base numérica, como base 2 para binario o base 8 para octal. Si no se especifica la base, por defecto utiliza la base 10, que es decimal.

```js
const num = 10;
console.log(num.toString(2)); // "1010"(binary)
```

## Constructor `Number`

- **Definición**: El constructor `Number` se utiliza para crear un objeto número. El objeto número contiene algunas propiedades y métodos útiles, como los métodos `isNaN` y `toFixed`. La mayoría de las veces, utilizarás el constructor `Number` para convertir otros tipos de datos al tipo de dato número.

```js
const myNum = new Number("34");
console.log(typeof myNum); // "object"

const num = Number('100');
console.log(num); // 100

console.log(typeof num); // number
```

## Buenas prácticas para nombrar variables y funciones

- **camelCasing**: Por convención, los desarrolladores de JavaScript utilizan camel case para nombrar variables y funciones. El camel case consiste en que la primera palabra está completamente en minúsculas y las siguientes palabras comienzan con mayúscula. Ej. `isLoading`.

- **Nombrar booleanos**: Para las variables booleanas, es una práctica común utilizar prefijos como `"is"`, `"has"` o `"can"`.

```js
let isLoading = true;
let hasPermission = false;
let canEdit = true;
```

- **Nombrar funciones**: Para las funciones, el nombre debería indicar claramente qué hace la función. Para las funciones que devuelven un booleano (a menudo llamadas predicados), puedes utilizar los mismos prefijos `"is"`, `"has"` o `"can"`. Cuando tienes funciones que recuperan datos, es común comenzar con la palabra `"get"`. Cuando tienes funciones que establecen datos, es común comenzar con la palabra `"set"`. Para las funciones que manejan eventos, puedes utilizar el prefijo `"handle"` o el sufijo `"Handler"`.

```js
function getUserData() { /* ... */ }

function isValidEmail(email) { /* ... */ }

function getProductDetails(productId) { /* ... */ }

function setUserPreferences(preferences) { /* ... */ }

function handleClick() { /* ... */ }
```

- **Nombrar variables dentro de bucles**: Al nombrar variables iteradoras en bucles, es común utilizar letras individuales como `i`, `j` o `k`.

```js
for (let i = 0; i < array.length; i++) { /* ... */ }
```

## Trabajar con arrays dispersos

- **Definición**: Es posible tener arrays con posiciones vacías. Las posiciones vacías se definen como posiciones que no contienen nada. Esto es diferente de las posiciones de un array cuyo valor es `undefined`. Este tipo de arrays se conocen como arrays dispersos.

```js
const sparseArray = [1, , , 4];
console.log(sparseArray.length); // 4
```

## Linters y formateadores

- **Linters**: Un linter es una herramienta de análisis estático de código que detecta errores de programación, bugs, errores de estilo y construcciones sospechosas. Un ejemplo de linter común sería ESLint.

- **Formateadores**: Los formateadores son herramientas que dan formato automáticamente a tu código para adaptarlo a una guía de estilo específica. Un ejemplo de formateador común sería Prettier.

## Gestión de memoria

- **Definición**: La gestión de memoria es el proceso de controlar la memoria, asignándola cuando se necesita y liberándola cuando ya no es necesaria. JavaScript utiliza una gestión automática de memoria. Esto significa que JavaScript (más concretamente, el motor de JavaScript de tu navegador web) se encarga de la asignación y liberación de memoria por ti. No tienes que liberar memoria explícitamente en tu código. Este proceso automático suele denominarse "recolección de basura".

## Clausuras

- **Definición**: Una clausura es una función que tiene acceso a las variables de su ámbito léxico exterior (que la contiene), incluso después de que la función exterior haya terminado de ejecutarse.

```js
function outerFunction(x) {
  let y = 10;
  function innerFunction() {
    console.log(x + y);
  }
  return innerFunction;
}

let closure = outerFunction(5);
closure(); // 15
```

## Palabra clave `var` y hoisting

- **Definición**: `var` era la forma original de declarar variables antes de 2015. Pero había algunos problemas relacionados con `var` en cuanto al ámbito, la redeclaración y otros aspectos. Por eso, la programación moderna en JavaScript utiliza `let` y `const` en su lugar.

- **Redeclarar variables con `var`**: Si intentas redeclarar una variable utilizando `let`, obtendrás un `SyntaxError`. Pero con `var`, se permite redeclarar una variable.

```js
// Uncaught SyntaxError: Identifier 'num' has already been declared 
let num = 19;
let num = 18;

var myNum = 5;
var myNum = 10; // Esto está permitido y no genera un error

console.log(myNum) // 10
```

- **`var` y ámbito**: Las variables declaradas con `var` dentro de un bloque (como una sentencia `if` o un bucle `for`) siguen siendo accesibles fuera de ese bloque.

```js
if (true) {
  var num = 5;
}
console.log(num); // 5
```

- **Hoisting**: Este es el comportamiento predeterminado de JavaScript de mover las declaraciones al principio de sus respectivos ámbitos durante la fase de compilación, antes de que se ejecute el código. Cuando declaras una variable utilizando la palabra clave `var`, JavaScript eleva la declaración al principio de su ámbito.

```js
console.log(num); // undefined
var num = 5;
console.log(num); // 5
```

Cuando declaras una función utilizando la sintaxis de declaración de función, tanto el nombre de la función como el cuerpo de la función se elevan. Esto significa que puedes llamar a una función antes de haberla declarado en tu código.

```js
sayHello(); // "Hello, World!"

function sayHello() {
  console.log("Hello, World!");
}
```

Las declaraciones de variables realizadas con `let` o `const` se elevan, pero no se inicializan, y no puedes acceder a ellas antes de la declaración real en tu código. Este comportamiento suele denominarse "zona muerta temporal".

```js
console.log(num); // Throws a ReferenceError
let num = 10;
```

## Trabajar con imports, exports y módulos

- **Módulo**: Es una unidad de código independiente que encapsula funciones, clases o variables relacionadas. Para crear un módulo, escribes tu código JavaScript en un archivo separado.

- **Exports**: Cualquier variable, función o clase que quieras poner a disposición de otras partes de tu aplicación debe ser exportada explícitamente utilizando la palabra clave `export`. Hay dos tipos de exportación: exportación con nombre y exportación por defecto.

- **Imports**: Para utilizar los elementos exportados en otra parte de tu aplicación, debes importarlos utilizando la palabra clave `import`. Los tipos pueden ser importación con nombre, importación por defecto e importación de espacio de nombres.

```js
// Dentro de un archivo llamado math.js, exportamos las siguientes funciones:

// Exportación con nombre
export function add(num1, num2) {
  return num1 + num2;
}

// Exportación por defecto
export default function subtract(num1, num2) {
  return num1 - num2;
}

// Dentro de otro archivo, podemos importar las funciones de math.js.

// Importación con nombre - Esta línea importa la función add.
// El nombre de la función debe coincidir exactamente con el exportado desde math.js.
import { add } from './math.js';

// Importación por defecto - Esta línea importa la función subtract.
// El nombre de la función puede ser cualquiera.
import subtractFunc from './math.js';

// Importación de espacio de nombres - Esta línea importa todo desde el archivo.
import * as Math from './math.js';

console.log(add(5, 3)); // 8
console.log(subtractFunc(5, 3)); // 2
console.log(Math.add(5, 3)); // 8
console.log(Math.subtract(5, 3)); // 2
```