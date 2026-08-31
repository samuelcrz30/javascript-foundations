## Funciones de JavaScript

* Las funciones son bloques de código reutilizables que realizan una tarea específica.
* Las funciones se pueden definir utilizando la palabra clave `function`, seguida de un nombre, una lista de parámetros y un bloque de código que realiza la tarea.

```js
function addNumbers(x, y, z) {
  return x + y + z;
}

console.log(addNumbers(5, 3, 8)); // Output: 16
```

* Los argumentos son valores que se pasan a una función cuando se llama.
* Una llamada a una función es el proceso de ejecutar una función en un programa especificando el nombre de la función seguido de paréntesis, incluyendo opcionalmente argumentos dentro de los paréntesis.
* Cuando una función termina su ejecución, siempre devolverá un valor.
* De forma predeterminada, el valor de retorno de una función es `undefined`.
* La palabra clave `return` se utiliza para especificar el valor que se devolverá desde la función y termina la ejecución de la función.
* Los parámetros predeterminados permiten que las funciones tengan valores predefinidos que se utilizarán si no se proporciona un argumento cuando se llama a la función. Esto hace que las funciones sean más flexibles y evita errores en los casos en los que ciertos argumentos puedan omitirse.

```js
const calculateTotal = (amount, taxRate = 0.05) => {
  return amount + (amount * taxRate);
};

console.log(calculateTotal(100)); // Output: 105
```

* Las funciones anónimas son funciones sin nombre que se pueden asignar a variables. Al asignarlas a variables, puedes reutilizarlas en cualquier lugar donde la variable sea accesible.

```js
const multiplyNumbers = function(firstNumber, secondNumber) {
  return firstNumber * secondNumber;
};

console.log(multiplyNumbers(4, 5)); // Output: 20
```

## Funciones flecha (Arrow Functions)

* Las funciones flecha son una forma más concisa de escribir funciones en JavaScript.

```js
const calculateArea = (length, width) => {
  const area = length * width;
  return `The area of the rectangle is ${area} square units.`;
};

console.log(calculateArea(5, 10)); // Output: "The area of the rectangle is 50 square units."
```

* Al definir una función flecha, no necesitas utilizar la palabra clave `function`.
* Si utilizas un único parámetro, puedes omitir los paréntesis alrededor de la lista de parámetros.

```js
const cube = x => {
  return x * x * x;
};

console.log(cube(3)); // Output: 27
```

* Si el cuerpo de la función consta de una única expresión, puedes omitir las llaves y la palabra clave `return`.

```js
const square = number => number * number;

console.log(square(5)); // Output: 25
```

## Ámbito (Scope) en programación

* **Ámbito global (Global scope)**: Este es el ámbito más externo en JavaScript. Las variables declaradas en el ámbito global son accesibles desde cualquier parte del código y se denominan variables globales.
* **Ámbito local (Local scope)**: Se refiere a las variables declaradas dentro de una función. Estas variables solo son accesibles dentro de la función en la que se declaran y se denominan variables locales.
* **Ámbito de bloque (Block scope)**: Un bloque es un conjunto de sentencias encerradas entre llaves `{}`, como ocurre en las sentencias `if` o en los bucles.
* El ámbito de bloque con `let` y `const` proporciona un control aún más preciso sobre la accesibilidad de las variables, ayudando a prevenir errores y haciendo que tu código sea más predecible.
