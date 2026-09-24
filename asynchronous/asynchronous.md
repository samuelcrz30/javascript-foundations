# Repaso de JavaScript asíncrono

* **JavaScript síncrono** se ejecuta secuencialmente y espera a que termine la operación anterior antes de pasar a la siguiente.
* **JavaScript asíncrono** permite que varias operaciones se ejecuten en segundo plano sin bloquear el hilo principal.
* **Hilo (Thread)** es una secuencia de instrucciones que puede ejecutarse independientemente del flujo principal del programa.
* **Funciones callback** son funciones que se pasan como argumentos a otras funciones y se ejecutan después de que se complete la operación o como resultado de un evento.

## El motor de JavaScript y el entorno de ejecución de JavaScript

* El **motor de JavaScript** es un programa que ejecuta código JavaScript en un navegador web. Funciona como un conversor que toma tu código, lo transforma en instrucciones que el ordenador puede entender y actúa en consecuencia.
* V8 es un ejemplo de un motor de JavaScript desarrollado por Google.
* El **entorno de ejecución de JavaScript (JavaScript runtime)** es el entorno en el que se ejecuta el código JavaScript. Incluye el motor de JavaScript, que procesa y ejecuta el código, y funcionalidades adicionales como un navegador web o Node.js.

## La API Fetch

* La API Fetch permite a las aplicaciones web realizar solicitudes de red, normalmente para obtener o enviar datos al servidor. Proporciona un método `fetch()` que puedes utilizar para realizar estas solicitudes.
* Puedes obtener texto, imágenes, audio, JSON y otros tipos de datos utilizando la API Fetch.

## Métodos HTTP para la API Fetch

La API Fetch admite varios métodos HTTP para interactuar con el servidor. Los métodos más comunes son:

* **GET**: Se utiliza para obtener datos del servidor. Por defecto, la API Fetch utiliza el método `GET` para obtener datos.

```js
fetch('https://api.example.com/data')

```

Para utilizar los datos obtenidos, deben convertirse al formato JSON utilizando el método `.json()`:

```js
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))

```

En este código, `fetch()` devuelve una Promise, y el controlador `.then()` convierte la respuesta resuelta al formato JSON.

* **POST**: Se utiliza para enviar datos al servidor. El método `POST` se utiliza para crear nuevos recursos en el servidor.

```js
fetch('https://api.example.com/users', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    name: 'John Doe',
    email: 'john@example.com'
  })
})

```

En este ejemplo, estamos enviando una solicitud `POST` para crear un nuevo usuario. Hemos especificado el método como `POST`, establecido las cabeceras correspondientes e incluido un cuerpo con los datos que queremos enviar. El cuerpo debe ser un string, por lo que utilizamos `JSON.stringify()` para convertir nuestro objeto en un string JSON.

* **PUT**: Se utiliza para actualizar datos en el servidor. El método `PUT` se utiliza para actualizar recursos existentes en el servidor.

```js
fetch('https://api.example.com/users/45', {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    name: 'John Smith',
    email: 'john@example.com'
  })
})

```

En este ejemplo, estamos actualizando el ID `45`, que se especifica al final de la URL. Hemos utilizado el método `PUT` en el código y también hemos especificado los datos como el cuerpo que se utilizará para actualizar los datos identificados.

* **DELETE**: Se utiliza para eliminar datos del servidor. El método `DELETE` se utiliza para eliminar recursos del servidor.

```js
fetch('https://api.example.com/users/45', {
  method: 'DELETE'
})

```

En este ejemplo, estamos enviando una solicitud `DELETE` para eliminar un usuario con el ID `45`.

## Promise y encadenamiento de Promises

* **Promises** son objetos que representan la finalización o el fallo eventual de una operación asíncrona y su valor resultante. El valor de la Promise solo se conoce cuando la operación asíncrona ha terminado.
* Aquí tienes un ejemplo para crear una Promise sencilla:

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Data received successfully');
  }, 2000);
});

```

* El método `.then()` se utiliza en una Promise para especificar qué debe ocurrir cuando la Promise se cumple, mientras que `.catch()` se utiliza para gestionar cualquier error que ocurra.
* Aquí tienes un ejemplo de uso de `.then()` y `.catch()` con una Promise:

```js
promise
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error(error);
  });

```

En el ejemplo anterior, el método `.then()` se utiliza para mostrar los datos recibidos de la Promise, mientras que el método `.catch()` se utiliza para mostrar cualquier error que ocurra.

* **Encadenamiento de Promises**: Una de las características más potentes de las Promises es que podemos encadenar varias operaciones asíncronas. Cada `.then()` puede devolver una nueva Promise, lo que permite realizar una secuencia de operaciones asíncronas una después de otra.
* Aquí tienes un ejemplo de encadenamiento de Promises:

```js
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => {
    console.log(data);
    return fetch('https://api.example.com/other-data');
  })
  .then(response => response.json())
  .then(otherData => {
    console.log(otherData);
  })
  .catch(error => {
    console.error(error);
  });

```

En el ejemplo anterior, primero obtenemos datos de una URL, después obtenemos datos de otra URL basándonos en la primera respuesta y, finalmente, mostramos los segundos datos recibidos.

El método `catch` gestionaría cualquier error que ocurra durante el proceso. Esto significa que no es necesario añadir gestión de errores a cada paso, lo que puede simplificar considerablemente el código.

## Usar `async/await` para gestionar Promises

`async`/`await` facilita la escritura y lectura de código asíncrono y está construido sobre las Promises.

* **async**: La palabra clave `async` se utiliza para definir una función asíncrona. Una función `async` devuelve una Promise, que se resuelve con el valor devuelto por la función `async`.
* **await**: La palabra clave `await` se utiliza dentro de una función `async` para pausar la ejecución de la función hasta que la Promise se resuelva. Solo puede utilizarse dentro de una función `async`.
* Aquí tienes un ejemplo de uso de `async/await`:

```js
async function delayedGreeting(name) {
  console.log("A Messenger entered the chat...");
  await new Promise(resolve => setTimeout(resolve, 2000));
  console.log(`Hello, ${name}!`);
}

delayedGreeting("Alice");
console.log("First Printed Message!");

```

En el ejemplo anterior, la función `delayedGreeting` es una función `async` que hace una pausa de 2 segundos antes de mostrar el mensaje de saludo. La palabra clave `await` se utiliza para pausar la ejecución de la función hasta que la `Promise` se resuelva.

* Una de las mayores ventajas de `async/await` es la gestión de errores mediante bloques `try/catch`. Aquí tienes un ejemplo:

```js
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

fetchData();

```

En el ejemplo anterior, el bloque `try` contiene el código que podría producir un error y el bloque `catch` gestiona el error si ocurre. Esto hace que la gestión de errores sea más sencilla y fácil de leer.

## El atributo `async`

* El atributo `async` indica al navegador que descargue el archivo de script de forma asíncrona mientras continúa procesando el documento HTML.
* Una vez descargado el script, el procesamiento del HTML se pausa, se ejecuta el script y, después, continúa el procesamiento del HTML.
* Debes utilizar `async` para scripts independientes en los que el orden de ejecución no sea importante.

## El atributo `defer`

* El atributo `defer` también descarga el script de forma asíncrona, pero retrasa la ejecución del script hasta que el documento HTML se haya procesado completamente.
* Los scripts con `defer` mantienen el orden de ejecución en el que aparecen en el documento HTML.
* Es importante tener en cuenta que los atributos `async` y `defer` se ignoran en scripts inline y solo funcionan con archivos de script externos.
* Cuando están presentes los atributos `async` y `defer`, el atributo `async` tiene prioridad.

## API de Geolocalización

* La API de Geolocalización proporciona una forma para que los sitios web soliciten la ubicación del usuario.
* El siguiente ejemplo muestra el método `getCurrentPosition()` de la API, que se utiliza para obtener la ubicación actual del usuario.

```js
navigator.geolocation.getCurrentPosition(
  (position) => {
    console.log("Latitude: " + position.coords.latitude);
    console.log("Longitude: " + position.coords.longitude);
  },
  (error) => {
    console.log("Error: " + error.message);
  }
);

```

En este código, estamos llamando a `getCurrentPosition` y pasándole una función que será llamada cuando la posición se obtenga correctamente.

El objeto `position` contiene una variedad de información, pero aquí hemos seleccionado únicamente `latitude` y `longitude`.

Si existe algún problema al obtener la `position`, el error se mostrará en la consola.

* Es importante respetar la privacidad del usuario y solicitar su ubicación únicamente cuando sea necesario.
