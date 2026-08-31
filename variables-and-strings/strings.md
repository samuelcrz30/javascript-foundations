## Conceptos básicos de Strings

- **Definición**: Un string es una secuencia de caracteres encerrada entre comillas simples, comillas dobles o backticks. Los strings son tipos de datos primitivos y son inmutables. La inmutabilidad significa que, una vez creado un string, no puede ser modificado.
- **Acceder a caracteres de un String**: Para acceder a un carácter de un string puedes utilizar la notación de corchetes y pasar el número de índice. Un índice es la posición de un carácter dentro de un string, y está basado en cero.

```js
const developer = "Jessica";
console.log(developer[0]); // J
````

* **`\n` (Carácter de nueva línea)**: Puedes crear una nueva línea en un string utilizando el carácter de nueva línea `\n`.

```js
const poem = "Roses are red,\nViolets are blue,\nJavaScript is fun,\nAnd so are you.";
console.log(poem);
```

* **Escapar Strings**: Puedes escapar caracteres en un string colocando barras invertidas (`\`) delante de las comillas.

```js
const statement = "She said, \"Hello!\"";
console.log(statement); // She said, "Hello!"
```

## Template Literals (Strings de plantilla) e interpolación de Strings

* **Definición**: Los template literals se definen con backticks (`). Permiten una manipulación más sencilla de strings, incluyendo la posibilidad de insertar variables directamente dentro de un string, una característica conocida como interpolación de strings.

```js
const name = "Jessica";
const greeting = `Hello, ${name}!`; 
console.log(greeting); // "Hello, Jessica!"
```

## ASCII, el método `charCodeAt()` y el método `fromCharCode()`

* **ASCII**: ASCII (American Standard Code for Information Interchange) es un estándar de codificación de caracteres utilizado para representar caracteres básicos del inglés mediante valores numéricos. Las lecciones anteriores introducen `charCodeAt()` y `fromCharCode()` utilizando ejemplos de ASCII.
* **Unicode**: Los strings de JavaScript utilizan Unicode internamente, específicamente la codificación UTF-16. Para los primeros 128 caracteres (letras latinas básicas, dígitos y símbolos comunes), los valores Unicode coinciden con los códigos ASCII. Por eso los ejemplos basados en ASCII siguen funcionando en JavaScript.
* **El método `charCodeAt()`**: Este método devuelve la unidad de código UTF-16 del carácter situado en un índice específico. Para los caracteres latinos básicos, este valor coincide con el código ASCII.

```js
const letter = "A";
console.log(letter.charCodeAt(0));  // 65
```

* **El método `fromCharCode()`**: Este método convierte un código ASCII en su carácter correspondiente.

```js
const char = String.fromCharCode(65);
console.log(char);  // A
```

## Otros métodos comunes de Strings

* **El método `indexOf()`**: Este método se utiliza para buscar una subcadena dentro de un string. Si se encuentra la subcadena, `indexOf` devuelve el índice (o posición) de la primera aparición de esa subcadena. Si no se encuentra la subcadena, `indexOf` devuelve -1, lo que indica que la búsqueda no tuvo éxito.

```js
const text = "The quick brown fox jumps over the lazy dog.";
console.log(text.indexOf("fox")); // 16
console.log(text.indexOf("cat")); // -1
```

* **El método `includes()`**: Este método se utiliza para comprobar si un string contiene una subcadena específica. Si la subcadena se encuentra dentro del string, el método devuelve `true`. De lo contrario, devuelve `false`.

```js
const text = "The quick brown fox jumps over the lazy dog.";
console.log(text.includes("fox")); // true
console.log(text.includes("cat")); // false
```

* **El método `slice()`**: Este método extrae una parte de un string y devuelve un nuevo string, sin modificar el string original. Recibe dos parámetros: el índice inicial y el índice final opcional.

```js
const text = "freeCodeCamp";
console.log(text.slice(0, 4));  // "free"
console.log(text.slice(4, 8));  // "Code"
console.log(text.slice(8, 12)); // "Camp"
```

* **El método `toUpperCase()`**: Este método convierte todos los caracteres a letras mayúsculas y devuelve un nuevo string con todos los caracteres en mayúsculas.

```js
const text = "Hello, world!";
console.log(text.toUpperCase()); // "HELLO, WORLD!"
```

* **El método `toLowerCase()`**: Este método convierte todos los caracteres de un string a minúsculas.

```js
const text = "HELLO, WORLD!"
console.log(text.toLowerCase()); // "hello, world!"
```

* **El método `replace()`**: Este método permite encontrar un valor específico (como una palabra o carácter) en un string y reemplazarlo por otro valor. El método devuelve un nuevo string con el reemplazo y deja el original sin modificar porque los strings de JavaScript son inmutables.

```js
const text = "I like cats";
console.log(text.replace("cats", "dogs")); // "I like dogs"
```

* **El método `replaceAll()`**: Este método permite encontrar todas las apariciones de un valor específico (una palabra, carácter o patrón) en un string y reemplazarlas por otro valor. Funciona como `replace()`, pero en lugar de detenerse después de la primera coincidencia, actualiza todas las coincidencias encontradas en el string.

```js
const text = "I love cats and cats are so much fun!";
console.log(text.replaceAll("cats", "dogs")); // "I love dogs and dogs are so much fun!"
```

* **El método `repeat()`**: Este método se utiliza para repetir un string un número específico de veces.

```js
const text = "Hello";
console.log(text.repeat(3)); // "HelloHelloHello"
```

* **El método `trim()`**: Este método se utiliza para eliminar los espacios en blanco tanto del principio como del final de un string.

```js
const text = "  Hello, world!  ";
console.log(text.trim()); // "Hello, world!"
```

* **El método `trimStart()`**: Este método elimina los espacios en blanco del principio (o "inicio") del string.

```js
const text = "  Hello, world!  ";
console.log(text.trimStart()); // "Hello, world!  "
```

* **El método `trimEnd()`**: Este método elimina los espacios en blanco del final del string.

```js
const text = " Hello, world! ";
console.log(text.trimEnd()); // "  Hello, world!"
```

* **El método `prompt()`**: Este método de `window` se utiliza para obtener información de un usuario mediante un cuadro de diálogo. Este método recibe dos argumentos. El primero es el mensaje que aparecerá dentro del cuadro de diálogo, normalmente solicitando al usuario que introduzca información. El segundo es un valor predeterminado que es opcional y que rellenará inicialmente el campo de entrada.

```js
const answer = window.prompt("What's your favorite animal?");
```
