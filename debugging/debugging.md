# Repaso de depuración de JavaScript

## Tipos comunes de mensajes de error

* **SyntaxError**: Estos errores ocurren cuando escribes algo incorrectamente en tu código, como cuando falta un paréntesis o un corchete. Piensa en ello como un error gramatical en una frase.

```js
const arr = ["Beau", "Quincy" "Tom"]

```

* **ReferenceError**: Hay varios tipos de errores de referencia, provocados de diferentes maneras. El primer tipo de error de referencia sería utilizar variables que no están definidas. Otro ejemplo de un `ReferenceError` es intentar acceder a una variable declarada con `let` o `const` antes de que haya sido definida.

```js
console.log(num);
const num = 50;

```

* **TypeError**: Estos errores ocurren cuando intentas realizar una operación sobre un tipo incorrecto.

```js
const developerObj = {
  name: "Jessica",
  country: "USA",
  isEmployed: true
};

developerObj.map()

```

* **RangeError**: Estos errores ocurren cuando tu código intenta utilizar un valor que está fuera del rango que JavaScript puede manejar.

```js
const arr = [];
arr.length = -1; 

```

## La instrucción `throw`

* **Definición**: La instrucción `throw` en JavaScript se utiliza para lanzar una excepción definida por el usuario. Una excepción en programación ocurre cuando sucede un evento inesperado que interrumpe el flujo normal del programa.

```js
function validateNumber(input) {
  if (typeof input !== "number") {
    throw new TypeError("Expected a number, but received " + typeof input);
  }
  return input * 2;
}

console.log(validateNumber("Naomi"));   // TypeError: Expected a number, but received string

```

## `try...catch...finally`

* **Definición**: El bloque `try` se utiliza para envolver código que podría producir un error. Actúa como un espacio seguro para intentar algo que podría fallar. El bloque `catch` captura y gestiona los errores que ocurren en el bloque `try`. Puedes utilizar el objeto de error dentro de `catch` para inspeccionar qué salió mal. El bloque `finally` se ejecuta después de los bloques `try` y `catch`, independientemente de si ocurrió un error. Se utiliza habitualmente para tareas de limpieza, como cerrar archivos o liberar recursos.

```js
function processInput(input) {
  if (typeof input !== "string") {
    throw new TypeError("Input must be a string.");
  }

  return input.toUpperCase();
}

try {
  console.log("Starting to process input...");
  const result1 = processInput("hello");
  console.log("Processed result:", result1);  // HELLO
  const result2 = processInput(9);  // throws TypeError
  console.log("Processed result:", result2);  // not executed
} catch (error) {
  console.error("Error occurred:", error.message);
} 

```

## Técnicas de depuración

* **Instrucción `debugger`**: Esta instrucción permite pausar tu código en una línea específica para investigar qué está ocurriendo en el programa.

```js
let firstNumber = 5;
let secondNumber = 10;

debugger; // Code execution pauses here
let sum = firstNumber + secondNumber;

console.log(sum);

```

* **Breakpoints**: Los breakpoints permiten pausar la ejecución de tu código en una línea específica que elijas. Después de la pausa, puedes inspeccionar variables, evaluar expresiones y examinar la pila de llamadas.
* **Watchers**: Las expresiones de seguimiento te permiten monitorizar los valores de variables o expresiones a medida que se ejecuta el código, incluso si están fuera del ámbito actual.
* **Profiling**: El profiling te ayuda a identificar cuellos de botella de rendimiento permitiéndote capturar capturas de pantalla y registrar el uso de la CPU, las llamadas a funciones y el tiempo de ejecución.
* **`console.dir()`**: Este método se utiliza para mostrar una lista interactiva de las propiedades de un objeto JavaScript especificado. Muestra una lista jerárquica que puede expandirse para ver todas las propiedades anidadas.

```js
console.dir(document);

```

* **`console.table()`**: Este método muestra datos tabulares como una tabla en la consola. Toma un argumento obligatorio, que debe ser un array o un objeto, y un argumento opcional para especificar qué propiedades (columnas) mostrar.
