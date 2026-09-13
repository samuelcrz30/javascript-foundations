# Repaso de funciones de orden superior de JavaScript

## Funciones callback y el método `forEach`

- **Definición**: En JavaScript, una función callback es una función que se pasa como argumento a otra función y se ejecuta después de que la función principal haya terminado su ejecución.

- **Método `forEach()`**: Este método se utiliza para iterar sobre cada elemento de un array y realizar una operación sobre cada elemento. La función callback de `forEach` puede recibir hasta tres argumentos: el elemento actual, el índice del elemento actual y el array sobre el que se llamó a `forEach`.

```js
const numbers = [1, 2, 3, 4, 5];

// Resultado: 2 4 6 8 10
numbers.forEach((number) => {
  console.log(number * 2);
});
```

## Funciones de orden superior

- **Definición**: Una función de orden superior recibe una o más funciones como argumentos y devuelve una función o un valor como resultado.

```js
function operateOnArray(arr, operation) {
  const result = [];
  for (let i = 0; i < arr.length; i++) {
    result.push(operation(arr[i]));
  }
  return result;
}

function double(x) {
  return x * 2;
}

const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = operateOnArray(numbers, double);
console.log(doubledNumbers); // [2, 4, 6, 8, 10]
```

- **Método `map()`**: Este método se utiliza para crear un nuevo array aplicando una función determinada a cada elemento del array original. La función callback puede aceptar hasta tres argumentos: el elemento actual, el índice del elemento actual y el array sobre el que se llamó a `map`.

```js
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((num) => num * 2);

console.log(numbers); // [1, 2, 3, 4, 5]
console.log(doubled); // [2, 4, 6, 8, 10]
```

- **Método `filter()`**: Este método se utiliza para crear un nuevo array con los elementos que superan una prueba especificada, lo que lo hace útil para extraer elementos selectivamente en función de determinados criterios. Al igual que el método `map`, la función callback del método `filter` acepta los mismos tres argumentos: el elemento actual que se está procesando, el índice y el array.

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const evenNumbers = numbers.filter((num) => num % 2 === 0);

console.log(evenNumbers); // [2, 4, 6, 8, 10]
```

- **Método `reduce()`**: Este método se utiliza para procesar un array y reducirlo a un único valor. Este único valor puede ser un número, una cadena de texto, un objeto o incluso otro array. El método `reduce()` funciona aplicando una función a cada elemento del array, en orden, pasando el resultado de cada cálculo al siguiente. Esta función suele denominarse función reductora. La función reductora recibe dos parámetros principales: un acumulador y el valor actual. El acumulador es donde almacenas el resultado acumulado de tus operaciones, y el valor actual es el elemento del array que se está procesando.

```js
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);

console.log(sum); // 15
```

## Encadenamiento de métodos

- **Definición**: El encadenamiento de métodos es una técnica de programación que permite llamar a múltiples métodos sobre el mismo objeto en una sola línea de código. Esta técnica puede hacer que tu código sea más legible y conciso, especialmente cuando realizas una serie de operaciones sobre el mismo objeto.

```js
const result = "  Hello, World!  "
  .trim()
  .toLowerCase()
  .replace("world", "JavaScript");

console.log(result); // "hello, JavaScript!"
```

## Trabajar con el método `sort`

- **Definición**: El método `sort` se utiliza para ordenar los elementos de un array y devolver una referencia al array ordenado. En este caso no se crea ninguna copia porque los elementos se ordenan directamente en el propio array.

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();

console.log(fruits); // ["Apple", "Banana", "Mango", "Orange"]
```

Si necesitas ordenar números, tendrás que proporcionar una función de comparación. El método `sort` convierte los elementos en cadenas de texto y después compara sus secuencias de valores de unidades de código UTF-16. Las unidades de código UTF-16 son los valores numéricos que representan los caracteres de la cadena. Algunos ejemplos de unidades de código UTF-16 son los números 65, 66 y 67, que representan respectivamente los caracteres `"A"`, `"B"` y `"C"`. Por eso, el número 200 aparece antes que el número 3 en un array, porque la cadena `"200"` aparece antes que la cadena `"3"` al comparar sus unidades de código UTF-16.

```js
const numbers = [414, 200, 5, 10, 3];

numbers.sort((a, b) => a - b);

console.log(numbers); // [3, 5, 10, 200, 414]
```

Los parámetros `a` y `b` son los dos elementos que se están comparando. La función de comparación debe devolver un valor negativo si `a` debe aparecer antes que `b`, un valor positivo si `a` debe aparecer después que `b`, y cero si `a` y `b` son iguales.

## Trabajar con los métodos `every` y `some`

- **Método `every()`**: Este método comprueba si todos los elementos de un array superan una prueba implementada por una función proporcionada. El método `every()` devuelve `true` si la función proporcionada devuelve `true` para todos los elementos del array. Si algún elemento no supera la prueba, el método devuelve inmediatamente `false` y deja de comprobar los elementos restantes.

```js
const numbers = [2, 4, 6, 8, 10];
const hasAllEvenNumbers = numbers.every((num) => num % 2 === 0);

console.log(hasAllEvenNumbers); // true
```

- **Método `some()`**: Este método comprueba si al menos un elemento supera la prueba. El método `some()` devuelve `true` en cuanto encuentra un elemento que supera la prueba. Si ningún elemento supera la prueba, devuelve `false`.

```js
const numbers = [1, 3, 5, 7, 8, 9];
const hasSomeEvenNumbers = numbers.some((num) => num % 2 === 0);

console.log(hasSomeEvenNumbers); // true
```