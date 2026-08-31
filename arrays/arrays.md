## Conceptos básicos de Arrays en JavaScript

* **Definición**: Un array de JavaScript es una colección ordenada de valores, cada uno identificado por un índice numérico. Los valores de un array de JavaScript pueden ser de diferentes tipos de datos, incluyendo números, strings, booleanos, objetos e incluso otros arrays. Los arrays son contiguos en memoria, lo que significa que todos los elementos se almacenan en un único bloque continuo de posiciones de memoria, permitiendo una indexación eficiente y un acceso rápido a los elementos mediante su índice.

```js
const developers = ["Jessica", "Naomi", "Tom"];
```

* **Acceder a elementos de Arrays**: Para acceder a elementos de un array, debes hacer referencia al array seguido de su número de índice dentro de corchetes. Los arrays de JavaScript utilizan índices basados en cero, lo que significa que el primer elemento está en el índice 0, el segundo elemento está en el índice 1, etc. Si intentas acceder a un índice que no existe en el array, JavaScript devolverá `undefined`.

```js
const developers = ["Jessica", "Naomi", "Tom"];
console.log(developers[0]) // "Jessica"
console.log(developers[1]) // "Naomi"

console.log(developers[10]) // undefined
```

* **Propiedad `length`**: Esta propiedad se utiliza para devolver el número de elementos de un array.

```js
const developers = ["Jessica", "Naomi", "Tom"];
console.log(developers.length) // 3
```

* **Actualizar elementos de un Array**: Para actualizar un elemento de un array, utilizas el operador de asignación (`=`) para asignar un nuevo valor al elemento situado en un índice específico.

```js
const fruits = ['apple', 'banana', 'cherry'];
fruits[1] = 'blueberry';

console.log(fruits); // ['apple', 'blueberry', 'cherry']
```

## Arrays bidimensionales

* **Definición**: Un array bidimensional es, básicamente, un array de arrays. Se utiliza para representar datos que tienen una estructura natural similar a una cuadrícula, como un tablero de ajedrez, una hoja de cálculo o los píxeles de una imagen. Para acceder a un elemento de un array bidimensional, necesitas dos índices: uno para la fila y otro para la columna.

```js
const chessboard = [
    ['R', 'N', 'B', 'Q', 'K', 'B', 'N', 'R'],
    ['P', 'P', 'P', 'P', 'P', 'P', 'P', 'P'],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
    ['p', 'p', 'p', 'p', 'p', 'p', 'p', 'p'],
    ['r', 'n', 'b', 'q', 'k', 'b', 'n', 'r']
];

console.log(chessboard[0][3]); // "Q"
```

## Desestructuración de Arrays

* **Definición**: La desestructuración de arrays es una característica de JavaScript que permite extraer valores de arrays y asignarlos a variables de una forma más concisa y legible. Proporciona una sintaxis cómoda para desempaquetar los elementos de un array en variables independientes.

```js
const fruits = ["apple", "banana", "orange"];

const [first, second, third] = fruits;

console.log(first); // "apple"
console.log(second); // "banana"
console.log(third); // "orange"
```

* **Sintaxis Rest**: Esto permite capturar los elementos restantes de un array que no han sido desestructurados en un nuevo array.

```js
const fruits = ["apple", "banana", "orange", "mango", "kiwi"];
const [first, second, ...rest] = fruits;

console.log(first); // "apple"
console.log(second); // "banana"
console.log(rest); // ["orange", "mango", "kiwi"]
```

## Métodos comunes de Arrays

* **Método `push()`**: Este método se utiliza para añadir elementos al final del array y devuelve la nueva longitud.

```js
const desserts = ["cake", "cookies", "pie"];
desserts.push("ice cream");

console.log(desserts); // ["cake", "cookies", "pie", "ice cream"];
```

* **Método `pop()`**: Este método se utiliza para eliminar el último elemento de un array y devuelve el elemento eliminado. Si el array está vacío, el valor devuelto será `undefined`.

```js
const desserts = ["cake", "cookies", "pie"];
desserts.pop();

console.log(desserts); // ["cake", "cookies"];
```

* **Método `shift()`**: Este método se utiliza para eliminar el primer elemento de un array y devolver el elemento eliminado. Si el array está vacío, el valor devuelto será `undefined`.

```js
const desserts = ["cake", "cookies", "pie"];
desserts.shift();

console.log(desserts); // ["cookies", "pie"];
```

* **Método `unshift()`**: Este método se utiliza para añadir elementos al principio del array y devuelve la nueva longitud.

```js
const desserts = ["cake", "cookies", "pie"];
desserts.unshift("ice cream");

console.log(desserts); // ["ice cream", "cake", "cookies", "pie"];
```

* **Método `indexOf()`**: Este método es útil para encontrar el primer índice de un elemento específico dentro de un array. Si no se puede encontrar el elemento, devolverá `-1`.

```js
const fruits = ["apple", "banana", "orange", "banana"];
const index = fruits.indexOf("banana");

console.log(index); // 1
console.log(fruits.indexOf("not found")); // -1
```

* **Método `splice()`**: Este método se utiliza para añadir o eliminar elementos desde cualquier posición de un array. El valor devuelto por el método `splice()` será un array con los elementos eliminados del array. Si no se elimina nada, se devolverá un array vacío. Este método modifica el array original, modificándolo directamente en lugar de crear un nuevo array. El primer argumento especifica el índice en el que se comenzará a modificar el array. El segundo argumento es el número de elementos que deseas eliminar. Los argumentos siguientes son los elementos que deseas añadir.

```js
const colors = ["red", "green", "blue"];
colors.splice(1, 0, "yellow", "purple");

console.log(colors); // ["red", "yellow", "purple", "green", "blue"]
```

* **Método `includes()`**: Este método se utiliza para comprobar si un array contiene un valor específico. Este método devuelve `true` si el array contiene el elemento especificado y `false` en caso contrario.

```js
const programmingLanguages = ["JavaScript", "Python", "C++"];

console.log(programmingLanguages.includes("Python")); // true
console.log(programmingLanguages.includes("Perl")); // false
```

* **Método `concat()`**: Este método crea un nuevo array combinando dos o más arrays.

```js
const programmingLanguages = ["JavaScript", "Python", "C++"];
const newList = programmingLanguages.concat("Perl");

console.log(newList); // ["JavaScript", "Python", "C++", "Perl"]
```

* **Método `slice()`**: Este método devuelve un nuevo array que contiene una copia superficial de una parte del array original, especificada mediante índices de inicio y final. El nuevo array contiene referencias a los mismos elementos que el original (no duplicados). Esto significa que, si los elementos son primitivos (como números o strings), los valores se copian; pero si los elementos son objetos o arrays, se copian las referencias, no los objetos en sí.

```js
const programmingLanguages = ["JavaScript", "Python", "C++"];
const newList = programmingLanguages.slice(1);

console.log(newList); // ["Python", "C++"]
```

* **Sintaxis Spread**: La sintaxis spread se utiliza para crear copias superficiales de un array.

```js
const originalArray = [1, 2, 3];
const shallowCopiedArray = [...originalArray];

shallowCopiedArray.push(4);

console.log(originalArray); // [1, 2, 3]
console.log(shallowCopiedArray); // [1, 2, 3, 4]
```

* **Método `split()`**: Este método divide un string en un array de subcadenas y especifica dónde debe realizarse cada división basándose en un separador determinado. Si no se proporciona ningún separador, el método devuelve un array que contiene el string original como un único elemento.

```js
const str = "hello";
const charArray = str.split("");

console.log(charArray); // ["h", "e", "l", "l", "o"]
```

* **Método `reverse()`**: Este método invierte un array directamente.

```js
const desserts = ["cake", "cookies", "pie"];
console.log(desserts.reverse()); // ["pie", "cookies", "cake"]
```

* **Método `join()`**: Este método concatena todos los elementos de un array en un único string, separando cada elemento mediante un separador especificado. Si no se proporciona ningún separador, o se utiliza un string vacío (`""`), los elementos se unirán sin ningún separador.

```js
const reversedArray = ["o", "l", "l", "e", "h"];
const reversedString = reversedArray.join("");

console.log(reversedString); // "olleh"
```
