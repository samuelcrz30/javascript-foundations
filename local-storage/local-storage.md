# Repaso de Local Storage y CRUD

## Almacenamiento persistente

* **Definición**: El almacenamiento persistente hace referencia a una forma de guardar datos de manera que sigan disponibles incluso después de apagar el dispositivo o reiniciarlo.

## Crear, Leer, Actualizar, Eliminar (CRUD)

* **Crear**: Hace referencia al proceso de crear nuevos datos. Por ejemplo, en una aplicación web, esto podría ocurrir cuando un usuario añade una nueva publicación a un blog.
* **Leer**: Es la operación mediante la cual se recuperan datos de una base de datos. Por ejemplo, cuando visitas una publicación de un blog o ves tu perfil en un sitio web, estás realizando una operación de lectura para obtener y mostrar los datos almacenados en la base de datos.
* **Actualizar**: Consiste en modificar datos existentes en la base de datos. Un ejemplo sería editar una publicación de un blog o actualizar la información de tu perfil.
* **Eliminar**: Es la operación que elimina datos de una base de datos. Por ejemplo, cuando eliminas una publicación de un blog o una cuenta, estás realizando una operación de eliminación.

## Métodos HTTP

* **Definición**: HTTP significa Hypertext Transfer Protocol (Protocolo de Transferencia de Hipertexto) y es la base para la comunicación de datos en la web. Existen métodos HTTP que definen las acciones que se pueden realizar sobre recursos a través de la web. Los métodos comunes son GET, POST, PUT, PATCH, DELETE.
* **Método `GET`**: Se utiliza para obtener datos de un servidor.
* **Método `POST`**: Se utiliza para enviar datos a un servidor, lo que crea un nuevo recurso.
* **Método `PUT`**: Se utiliza para actualizar un recurso reemplazándolo por completo.
* **Método `PATCH`**: Se utiliza para actualizar parcialmente un recurso.
* **Método `DELETE`**: Se utiliza para eliminar registros de una base de datos.

## Propiedades `localStorage` y `sessionStorage`

* **API Web Storage**: Esta API proporciona un mecanismo para que los navegadores almacenen pares clave-valor directamente dentro del navegador, permitiendo a los desarrolladores almacenar información que puede utilizarse entre diferentes recargas de página y sesiones. Los dos componentes principales de la API Web Storage son las propiedades `localStorage` y `sessionStorage`.
* **Propiedad `localStorage`**: `localStorage` es la parte de la API Web Storage que permite que los datos persistan incluso después de cerrar la ventana del navegador o actualizar la página. Estos datos permanecen disponibles hasta que la aplicación o el usuario los elimina explícitamente.
* **Método `localStorage.setItem()`**: Este método se utiliza para almacenar un par clave-valor en `localStorage`.

```js
localStorage.setItem('username', 'Jessica');

```

* **Método `localStorage.getItem()`**: Este método se utiliza para recuperar el valor de una clave determinada de `localStorage`.

```js
localStorage.setItem('username', 'codingRules');

let username = localStorage.getItem('username');
console.log(username); // codingRules

```

* **Método `localStorage.removeItem()`**: Este método se utiliza para eliminar un elemento específico de `localStorage` utilizando su clave.

```js
localStorage.removeItem('username');

```

* **Método `localStorage.clear()`**: Este método se utiliza para eliminar todos los datos almacenados en `localStorage`.

```js
localStorage.clear();

```

* **Propiedad `sessionStorage`**: Almacena datos que duran únicamente durante la sesión actual y se eliminan cuando se cierra la pestaña o ventana del navegador.
* **Método `sessionStorage.setItem()`**: Este método se utiliza para almacenar un par clave-valor en `sessionStorage`.

```js
sessionStorage.setItem('cart', '3 items');

```

* **Método `sessionStorage.getItem()`**: Este método se utiliza para recuperar el valor de una clave determinada de `sessionStorage`.

```js
sessionStorage.setItem('cart', '3 items');

let cart = sessionStorage.getItem('cart');
console.log(cart); // '3 items'

```

* **Método `sessionStorage.removeItem()`**: Este método se utiliza para eliminar un elemento específico de `sessionStorage` utilizando su clave.

```js
sessionStorage.removeItem('cart');

```

* **Método `sessionStorage.clear()`**: Este método se utiliza para eliminar todos los datos almacenados en `sessionStorage`.

```js
sessionStorage.clear();

```

## Trabajando con Cookies

* **Definición**: Las cookies, también conocidas como cookies web o cookies del navegador, son pequeños fragmentos de datos que un servidor envía al navegador web de un usuario. Estas cookies se almacenan en el dispositivo del usuario y se envían de vuelta al servidor con las solicitudes posteriores. Las cookies son esenciales para ayudar a las aplicaciones web a mantener el estado y recordar información del usuario, lo cual es especialmente importante debido a que HTTP es un protocolo sin estado.
* **Cookies de sesión**: Estas cookies solo duran durante la sesión del usuario en el sitio web. Una vez que el usuario cierra el navegador o la pestaña, la cookie de sesión se elimina. Estas cookies suelen utilizarse para tareas como mantener a un usuario conectado durante su visita.
* **Cookies seguras**: Estas cookies solo se envían mediante HTTPS, lo que garantiza que no puedan ser interceptadas por un atacante durante su transmisión.
* **Cookies HttpOnly**: Estas cookies no pueden ser accedidas ni modificadas por JavaScript ejecutándose en el navegador, lo que las hace más seguras frente a ataques de Cross-Site Scripting (XSS).
* **Cabecera Set-Cookie**: Cuando visitas un sitio web, el servidor puede enviar una cabecera Set-Cookie en la respuesta HTTP. Esta cabecera indica al navegador que debe guardar una cookie con información específica. Por ejemplo, podría almacenar un ID único que ayude al sitio a reconocerte la próxima vez que lo visites.

Puedes establecer manualmente una cookie en JavaScript utilizando `document.cookie`:

```js
document.cookie = "organization=freeCodeCamp; expires=Fri, 31 Dec 2021 23:59:59 GMT; path=/";

```

Para eliminar una cookie, puedes establecer su fecha de expiración en un momento del pasado.

```js
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 GMT; path=/";

```

## API Cache

* **Definición**: La caché es el proceso de almacenar copias de archivos en una ubicación de almacenamiento temporal, de modo que puedan accederse más rápidamente. La API Cache se utiliza para almacenar solicitudes y respuestas de red, haciendo que las aplicaciones web funcionen de manera más eficiente e incluso puedan funcionar sin conexión. Forma parte de la API de Service Worker más amplia y es fundamental para crear Progressive Web Apps (PWAs) que puedan funcionar en condiciones de red poco fiables o lentas.

La API Cache es un mecanismo de almacenamiento que almacena objetos Request y Response. Cuando se realiza una solicitud a un servidor, la aplicación puede almacenar la respuesta y recuperarla posteriormente desde la caché en lugar de realizar una nueva solicitud de red. Esto reduce los tiempos de carga, ahorra ancho de banda y mejora la experiencia general del usuario.

* **Almacenamiento de caché**: Se utiliza para almacenar pares clave-valor de solicitudes HTTP y sus respuestas correspondientes. Esto permite recuperar de manera eficiente recursos solicitados anteriormente, reduciendo la necesidad de obtenerlos de la red en visitas posteriores y mejorando el rendimiento.
* **Cache-Control**: Los desarrolladores pueden definir durante cuánto tiempo debe mantenerse un recurso en caché y si debe volver a validarse o servirse directamente desde la caché.
* **Soporte sin conexión**: Mediante la API Cache, puedes crear aplicaciones web que funcionen sin conexión como primera opción. Por ejemplo, una PWA puede servir recursos almacenados en caché cuando el usuario está desconectado de la red.

## Patrones negativos y almacenamiento del lado del cliente

* **Seguimiento excesivo**: Hace referencia a la práctica de recopilar y almacenar una cantidad excesiva de datos del usuario en el almacenamiento del lado del cliente (como cookies, local storage o session storage) sin un consentimiento claro e informado o una necesidad legítima. Esto suele implicar realizar un seguimiento del comportamiento, las preferencias y las interacciones del usuario en múltiples sitios o sesiones, lo que puede afectar a la privacidad del usuario.
* **Fingerprinting del navegador**: Una técnica utilizada para rastrear e identificar usuarios individuales basándose en características únicas de su dispositivo y navegador, en lugar de depender de cookies u otros métodos de seguimiento tradicionales. A diferencia de las cookies, que se almacenan localmente en el dispositivo del usuario, el fingerprinting implica recopilar una serie de datos que pueden utilizarse para crear una "huella digital" distintiva de la sesión del navegador de un usuario.
* **Guardar contraseñas en LocalStorage**: Esto puede parecer un patrón negativo más evidente, pero almacenar cualquier dato sensible, como contraseñas, en el almacenamiento local supone un riesgo de seguridad. Local Storage no está cifrado y se puede acceder a él fácilmente. Por lo tanto, nunca debes almacenar ningún tipo de dato sensible ahí.

## IndexedDB

* **Definición**: IndexedDB se utiliza para almacenar datos estructurados en el navegador. Está integrado en los navegadores web modernos, permitiendo a las aplicaciones web almacenar y obtener objetos JavaScript de manera eficiente.

## Cache/Service Workers

* **Definición**: Un Service Worker es un script que se ejecuta en segundo plano y que está separado de tu página web. Puede interceptar solicitudes de red, acceder a la caché y hacer que la aplicación web funcione sin conexión. Es un componente clave de las Progressive Web Apps.
