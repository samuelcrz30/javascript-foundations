# Repaso de expresiones regulares de JavaScript

## Expresiones regulares y métodos comunes

* **Definición**: Las expresiones regulares, o Regex, se utilizan para crear un "patrón", que luego puedes utilizar para comprobar una cadena, extraer texto y mucho más.

```js
const regex = /freeCodeCamp/;

```

* **Constructor `RegExp`**: Cuando tu patrón o tus flags provienen de variables, puedes crear el mismo tipo de regex con el constructor `RegExp`. Acepta una cadena como patrón y una cadena de flags opcional.

```js
const pattern = "freeCodeCamp";
const flags = "gi";
const regex = new RegExp(pattern, flags);
console.log(regex); // /freeCodeCamp/gi

```

* **Método `test()`**: Este método acepta una cadena, que es la cadena que se comprobará para buscar coincidencias con la expresión regular. Este método devuelve un booleano si la cadena coincide con la regex.

```js
const regex = /freeCodeCamp/;
const test = regex.test("e");
console.log(test); // false

```

* **Método `match()`**: Este método acepta una expresión regular, aunque también puedes pasar una cadena que se convertirá en una expresión regular. El método `match` devuelve el array de coincidencias de la cadena.

```js
const regex = /freeCodeCamp/;
const match = "freeCodeCamp".match(regex);
console.log(match); // ['freeCodeCamp', index: 0, input: 'freeCodeCamp', groups: undefined]

```

* **Método `replace()`**: Este método acepta dos argumentos: la expresión regular con la que buscar la coincidencia (o una cadena) y la cadena con la que reemplazar la coincidencia (o una función que se ejecutará sobre cada coincidencia).

```js
const regex = /Jessica/;
const str = "Jessica is rly kewl";
const replaced = str.replace(regex, "freeCodeCamp");
console.log(replaced); // "freeCodeCamp is rly kewl"

```

* **Método `replaceAll`**: Este método se utiliza para reemplazar todas las apariciones de un patrón especificado por una nueva cadena. Este método producirá un error si le proporcionas una expresión regular sin el modificador global.

```js
const text = "I hate JavaScript! I hate programming!";
const newText = text.replaceAll("hate", "love");
console.log(newText);  // "I love JavaScript! I love programming!"

```

* **Método `matchAll`**: Este método se utiliza para obtener todas las coincidencias de una expresión regular determinada en una cadena, incluidos los grupos de captura, y las devuelve como un iterador. Un iterador es un objeto que te permite recorrer (o "iterar sobre") una colección de elementos.

```js
const str = "JavaScript, Python, JavaScript, Swift, JavaScript";
const regex = /JavaScript/g;

const iterator = str.matchAll(regex);

for (let match of iterator) {
  console.log(match[0]); // "JavaScript" for each match
}

```

## Modificadores de expresiones regulares

* **Definición**: Los modificadores, a menudo llamados "flags", modifican el comportamiento de una expresión regular.
* **Flag `i`**: Esta flag hace que una regex ignore las mayúsculas y minúsculas.

```js
const regex = /freeCodeCamp/i;
console.log(regex.test("freecodecamp")); // true
console.log(regex.test("FREECODECAMP")); // true

```

* **Flag `g`**: Esta flag, o modificador global, permite que tu expresión regular coincida con un patrón más de una vez.

```js
const regex = /freeCodeCamp/gi;
console.log(regex.test("freeCodeCamp")); // true
console.log(regex.test("freeCodeCamp is great")); // false

```

* **Definición de anchor**: El anchor `^`, al principio de la expresión regular, indica "coincidir con el inicio de la cadena". El `$`, al final de la expresión regular, indica "coincidir con el final de la cadena".

```js
const start = /^freeCodeCamp/i;
const end = /freeCodeCamp$/i;
console.log(start.test("freecodecamp")); // true
console.log(end.test("freecodecamp")); // true

```

* **Flag `m`**: Los anchors buscan el principio y el final de toda la cadena. Pero puedes hacer que una regex gestione múltiples líneas con la flag `m`, o modificador multilínea.

```js
const start = /^freecodecamp/im;
const end = /freecodecamp$/im;
const str = `I love 
freecodecamp
it's my favorite
`;

console.log(start.test(str)); // true
console.log(end.test(str)); // true

```

* **Flag `d`**: Esta flag amplía la información que obtienes en un objeto de coincidencia.

```js
const regex = /freecodecamp/di;
const string = "we love freecodecamp isn't freecodecamp great?";
console.log(string.match(regex));

```

Y el resultado es:

```js
// [
//   'freecodecamp',
//   index: 8,
//   input: "we love freecodecamp isn't freecodecamp great?",
//   groups: undefined,
//   indices: [
//     0: [8, 20],
//     groups: undefined
//   ]
// ]

```

* **Flag `u`**: Esta flag amplía la funcionalidad de una expresión regular para permitirle coincidir con caracteres unicode especiales. La flag `u` te da acceso a clases especiales como `Extended_Pictographic` para coincidir con la mayoría de los emojis. También existe una flag `v`, que amplía aún más la funcionalidad de la coincidencia unicode.
* **Flag `y`**: El modificador sticky se comporta de forma muy similar al modificador global, pero con algunas excepciones. La principal es que una expresión regular global comenzará desde `lastIndex` y buscará en todo el resto de la cadena otra coincidencia, mientras que una expresión regular sticky devolverá `null` y restablecerá `lastIndex` a `0` si no hay inmediatamente una coincidencia en el `lastIndex` anterior.
* **Flag `s`**: El modificador de una sola línea permite que un carácter comodín, representado por un `.` en regex, coincida con saltos de línea, tratando efectivamente la cadena como una sola línea de texto.

## Clases de caracteres

* **Comodín `.`**: Las clases de caracteres son una sintaxis especial que puedes utilizar para coincidir con conjuntos o subconjuntos de caracteres. La primera clase de caracteres que deberías aprender es la clase comodín. El comodín está representado por un punto y coincide con CUALQUIER carácter individual EXCEPTO los saltos de línea. Para permitir que la clase comodín coincida con saltos de línea, recuerda que necesitarías utilizar la flag `s`.

```js
const regex = /a./;

```

* **`\d`**: Esto coincidirá con todos los dígitos (`0-9`) de una cadena.

```js
const regex = /\d/;

```

* **`\w`**: Se utiliza para coincidir con cualquier carácter de palabra (`a-zA-Z0-9_`) en una cadena. Un carácter de palabra se define como cualquier letra, de la a a la z o de la A a la Z, cualquier número del 0 al 9 o el carácter de guion bajo.

```js
const regex = /\w/;

```

* **`\s`**: La clase de espacios en blanco `\s` está representada por una barra invertida seguida de una `s`. Esta clase de caracteres coincidirá con cualquier espacio en blanco, incluyendo saltos de línea, espacios, tabulaciones y caracteres de espacio unicode especiales.
* **Negación de clases de caracteres especiales**: Para negar una de estas clases de caracteres, en lugar de utilizar una letra minúscula después de la barra invertida, puedes utilizar su equivalente en mayúscula. El siguiente ejemplo no coincide con un carácter numérico. En su lugar, coincide con cualquier carácter individual que NO sea un carácter numérico.

```js
const regex = /\D/;

```

* **Clases de caracteres personalizadas**: Puedes crear clases de caracteres personalizadas colocando el carácter con el que deseas coincidir dentro de un conjunto de corchetes.

```js
const regex = /[abcdf]/;

```

## Aserciones Lookahead y Lookbehind

* **Definición**: Las aserciones lookahead y lookbehind permiten coincidir con patrones específicos basándose en la presencia o ausencia de patrones circundantes.
* **Aserción Positive Lookahead**: Esta aserción coincidirá con un patrón cuando el patrón esté seguido por otro patrón. Para construir un positive lookahead, debes comenzar con el patrón que quieres coincidir. Después, utiliza paréntesis para envolver el patrón que quieres utilizar como condición. Después del paréntesis de apertura, utiliza `?=` para definir ese patrón como un positive lookahead.

```js
const regex = /free(?=code)/i;

```

* **Aserción Negative Lookahead**: Este es un tipo de condición utilizado en expresiones regulares para comprobar que un determinado patrón no aparece posteriormente en la cadena.

```js
const regex = /free(?!code)/i;

```

* **Aserción Positive Lookbehind**: Esta aserción coincidirá con un patrón únicamente si está precedido por otro patrón específico, sin incluir el patrón precedente en la coincidencia.

```js
const regex = /(?<=free)code/i;

```

* **Aserción Negative Lookbehind**: Esta aserción garantiza que un patrón no esté precedido por otro patrón específico. Coincide únicamente si el patrón especificado no está inmediatamente precedido por la secuencia indicada, sin incluir la secuencia precedente.

```js
const regex = /(?<!free)code/i;

```

## Cuantificadores de Regex

* **Definición**: Los cuantificadores en expresiones regulares especifican cuántas veces debe aparecer un patrón (o parte de un patrón). Ayudan a controlar el número de apariciones de caracteres o grupos en una coincidencia. El siguiente ejemplo se utiliza para hacer coincidir el carácter anterior exactamente cuatro veces.

```js
const regex = /^\d{4}$/;

```

* **`*`**: Coincide con 0 o más apariciones del elemento anterior.
* **`+`**: Coincide con 1 o más apariciones del elemento anterior.
* **`?`**: Coincide con 0 o 1 aparición del elemento anterior.
* **`{n}`**: Coincide exactamente con n apariciones del elemento anterior.
* **`{n,}`**: Coincide con n o más apariciones del elemento anterior.
* **`{n,m}`**: Coincide con entre n y m apariciones del elemento anterior.

## Grupos de captura y referencias inversas

* **Grupos de captura**: Un grupo de captura permite "capturar" una parte de la cadena coincidente para utilizarla como necesites. Los grupos de captura se definen mediante paréntesis que contienen el patrón que se quiere capturar, sin caracteres iniciales como los de un lookahead.

```js
const regex = /free(code)camp/i;

```

* **Grupos que no capturan**: Un grupo que no captura es similar a un grupo de captura, pero no almacena la parte coincidente de la cadena para utilizarla posteriormente. Los grupos que no capturan se definen mediante `(?:...)`.

```js
const regex = /free(?:code)camp/i;

```

* **Referencias inversas**: Una referencia inversa en expresiones regulares hace referencia a una forma de reutilizar una parte del patrón que coincidió anteriormente en la misma expresión. Permite hacer referencia a un grupo capturado (una parte del patrón entre paréntesis) mediante su número. Por ejemplo, `$1` hace referencia al primer grupo capturado.

```js
const regex = /free(co+de)camp/i;
console.log("freecoooooooodecamp".replace(regex, "paid$1world"));

```

* Puedes utilizar referencias inversas dentro de la propia regex para hacer coincidir el mismo texto capturado por un grupo anterior utilizando una barra invertida y el número del grupo de captura. Por ejemplo:

```js
const regex = /(hello) \1/i;
console.log(regex.test("hello hello")); // true
console.log(regex.test("hello world")); // false
```
