## Trabajando con bucles

* **Bucle `for`**: Este tipo de bucle se utiliza para repetir un bloque de código un determinado número de veces. Este bucle se divide en tres partes: la sentencia de inicialización, la condición y la sentencia de incremento/decremento. La sentencia de inicialización se ejecuta antes de que comience el bucle. Normalmente se utiliza para inicializar una variable contador. La condición se evalúa antes de cada iteración del bucle. Una iteración es un único recorrido a través del bucle. Si la condición es `true`, se ejecuta el bloque de código dentro del bucle. Si la condición es `false`, el bucle se detiene y pasas al siguiente bloque de código. La sentencia de incremento/decremento se ejecuta después de cada iteración del bucle. Normalmente se utiliza para incrementar o decrementar la variable contador.

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

* **Bucle `for...of`**: Este tipo de bucle se utiliza cuando necesitas recorrer los valores de un iterable. Algunos ejemplos de iterables son los arrays y las cadenas de texto.

```js
const numbers = [1, 2, 3, 4, 5];

for (const num of numbers) {
  console.log(num);
}
```

* **Bucle `for...in`**: Este tipo de bucle se utiliza mejor cuando necesitas recorrer las propiedades de un objeto. Este bucle iterará sobre todas las propiedades enumerables de un objeto, incluidas las propiedades heredadas y las propiedades no numéricas.

```js
const fruit = {
  name: 'apple',
  color: 'red',
  price: 0.99
};

for (const prop in fruit) {
  console.log(fruit[prop]);
}
```

* **Bucle `while`**: Este tipo de bucle ejecutará un bloque de código mientras la condición sea `true`.

```js
let i = 5;

while (i > 0) {
  console.log(i);
  i--;
}
```

* **Bucle `do...while`**: Este tipo de bucle ejecutará el bloque de código al menos una vez antes de comprobar la condición.

```js
let userInput;

do {
  userInput = prompt("Please enter a number between 1 and 10");
} while (Number(userInput) < 1 || Number(userInput) > 10);

alert("You entered a valid number!");
```

## Sentencias `break` y `continue`

* **Definición**: Una sentencia `break` se utiliza para salir de un bucle antes de tiempo, mientras que una sentencia `continue` se utiliza para omitir la iteración actual de un bucle y pasar a la siguiente.

```js
// Ejemplo de sentencia break
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;
  }
  console.log(i);
}

// Salida: 0, 1, 2, 3 y 4

// Ejemplo de sentencia continue 
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    continue;
  }
  console.log(i);
}

// Salida: 0, 1, 2, 3, 4, 6, 7, 8 y 9
```
