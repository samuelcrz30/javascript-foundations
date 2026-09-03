# Conceptos básicos de los objetos

**Definición:** Un objeto es una estructura de datos formada por propiedades. Una propiedad consta de una clave y un valor. Para acceder a los datos de un objeto puedes utilizar la notación de punto o la notación de corchetes.

```js
const person = {
  name: "Alice",
  age: 30,
  city: "New York"
};

console.log(person.name);  // Alice
console.log(person["name"]); // Alice
````

Para establecer una propiedad de un objeto existente puedes utilizar la notación de punto o la notación de corchetes junto con el operador de asignación.

```js
const person = {
  name: "Alice",
  age: 30
};

person.job = "Engineer"
person["hobby"] = "Knitting"
console.log(person);  // {name: 'Alice', age: 30, job: 'Engineer', hobby: 'Knitting'}
```

# Eliminar propiedades de un objeto

**Operador `delete`:** Este operador se utiliza para eliminar una propiedad de un objeto.

```js
const person = {
  name: "Alice",
  age: 30,
  job: "Engineer"
};

delete person.job;

console.log(person.job); // undefined
```

# Comprobar si un objeto tiene una propiedad

**Método `hasOwnProperty()`:** Este método devuelve un booleano que indica si el objeto tiene la propiedad especificada como propiedad propia.

```js
const person = {
  name: "Alice",
  age: 30
};

console.log(person.hasOwnProperty("name")); // true
console.log(person.hasOwnProperty("job")); // false
```

**Método `Object.hasOwn()`:** Esta es la forma moderna y recomendada de comprobar si un objeto tiene una propiedad como propia (no heredada). La sintaxis es `Object.hasOwn(object, propertyName)`. Devuelve `true` si la propiedad existe en el objeto y `false` si no existe, independientemente del valor de la propiedad. Esto hace que sea más seguro que `hasOwnProperty()` y más fiable que `if (obj.prop)` cuando los valores pueden ser `0`, `false`, `null` o `undefined`.

```js
const person = {
  name: "Alice",
  age: 30
};

console.log(Object.hasOwn(person, "name")); // true
console.log(Object.hasOwn(person, "job")); // false
```

Aquí tienes un ejemplo más detallado que muestra por qué `Object.hasOwn()` es más fiable que comprobar directamente el valor:

```js
const settings = {
  darkMode: false,
  fontSize: 0,
  language: null
};

// Object.hasOwn() detecta correctamente que estas propiedades existen
console.log(Object.hasOwn(settings, "darkMode")); // true (el valor es false, pero existe)
console.log(Object.hasOwn(settings, "fontSize")); // true (el valor es 0, pero existe)
console.log(Object.hasOwn(settings, "theme"));    // false (la propiedad nunca se añadió)

// ¡Usar if() directamente no es seguro para valores falsy!
if (settings.darkMode) {
  console.log("Dark mode on"); // NO se imprime — ¡puede llevar a conclusiones erróneas!
}

// Object.hasOwn() es la forma segura
if (Object.hasOwn(settings, "darkMode")) {
  console.log("darkMode exists, value is:", settings.darkMode); // darkMode exists, value is: false
}
```

**Operador `in`:** Este operador devuelve `true` si la propiedad existe en el objeto.

```js
const person = {
  name: "Bob",
  age: 25
};

console.log("name" in person);  // true
```

# Acceder a propiedades de objetos anidados

**Acceder a los datos:** Acceder a propiedades de objetos anidados implica utilizar la notación de punto o la notación de corchetes, al igual que al acceder a propiedades de objetos simples. Sin embargo, tendrás que encadenar estos accesores para profundizar en la estructura anidada.

```js
const person = {
  name: "Alice",
  age: 30,
  contact: {
    email: "alice@example.com",
    phone: {
      home: "123-456-7890",
      work: "098-765-4321"
    }
  }
};

console.log(person.contact.phone.work); // "098-765-4321"
```

# Tipos de datos primitivos y no primitivos

**Tipos de datos primitivos:** Estos tipos de datos incluyen números, cadenas de texto, booleanos, `null`, `undefined` y símbolos. Estos tipos se denominan "primitivos" porque representan valores individuales y no son objetos. Los valores primitivos son inmutables, lo que significa que una vez creados, su valor no puede cambiarse.

**Tipos de datos no primitivos:** En JavaScript, estos son objetos, que incluyen objetos normales, arrays y funciones. A diferencia de los primitivos, los tipos no primitivos pueden contener múltiples valores como propiedades o elementos.

# Métodos de los objetos

**Definición:** Los métodos de los objetos son funciones que están asociadas a un objeto. Se definen como propiedades de un objeto y pueden acceder y manipular los datos del objeto. La palabra clave `this` dentro del método hace referencia al propio objeto, permitiendo acceder a sus propiedades.

```js
const person = {
  name: "Bob",
  age: 30,
  sayHello: function() {
    return "Hello, my name is " + this.name;
  }
};

console.log(person.sayHello()); // "Hello, my name is Bob"
```

# Constructor de objetos

**Definición:** En JavaScript, un constructor es un tipo especial de función utilizado para crear e inicializar objetos. Se invoca con la palabra clave `new` y puede inicializar propiedades y métodos en el objeto recién creado. El constructor `Object()` crea un nuevo objeto vacío.

```js
new Object()
```

# Trabajar con el operador de encadenamiento opcional (`?.`)

**Definición:** Este operador permite acceder de forma segura a las propiedades de un objeto o llamar a métodos sin preocuparte de si existen.

```js
const user = {
  name: "John",
  profile: {
    email: "john@example.com",
    address: {
      street: "123 Main St",
      city: "Somewhere"
    }
  }
};

console.log(user.profile?.address?.street); // "123 Main St"
console.log(user.profile?.phone?.number);   // undefined
```

# Desestructuración de objetos

**Definición:** La desestructuración de objetos permite extraer valores de objetos y asignarlos a variables de una forma más concisa y legible.

```js
const person = { name: "Alice", age: 30, city: "New York" };

const { name, age } = person;

console.log(name); // Alice
console.log(age);  // 30
```

# Trabajar con JSON

**Definición:** JSON significa JavaScript Object Notation. Es un formato de datos ligero basado en texto que se utiliza habitualmente para intercambiar datos entre un servidor y una aplicación web.

```json
{
  "name": "Alice",
  "age": 30,
  "isStudent": false,
  "list of courses": ["Mathematics", "Physics", "Computer Science"]
}
```

**`JSON.stringify()`:** Este método se utiliza para convertir un objeto de JavaScript en una cadena JSON. Esto resulta útil cuando quieres almacenar o transmitir datos en un formato que pueda compartirse o transferirse fácilmente entre sistemas.

```js
const user = {
  name: "John",
  age: 30,
  isAdmin: true
};

const jsonString = JSON.stringify(user);
console.log(jsonString); // '{"name":"John","age":30,"isAdmin":true}'
```

**`JSON.parse()`:** Este método convierte una cadena JSON de nuevo en un objeto de JavaScript. Esto resulta útil cuando recuperas datos JSON de un servidor web o de `localStorage` y necesitas manipular los datos en tu aplicación.

```js
const jsonString = '{"name":"John","age":30,"isAdmin":true}';
const userObject = JSON.parse(jsonString);

// resultado: { name: 'John', age: 30, isAdmin: true }
console.log(userObject);
```
