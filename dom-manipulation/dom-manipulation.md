# Repaso de manipulación del DOM y eventos de clic con JavaScript

## Trabajar con el DOM y las Web APIs

* **API**: Una API (Interfaz de Programación de Aplicaciones) es un conjunto de reglas y protocolos que permiten a las aplicaciones de software comunicarse entre sí e intercambiar datos de manera eficiente.

* **Web API**: Las Web APIs están diseñadas específicamente para aplicaciones web. Estos tipos de API suelen dividirse en dos categorías principales: APIs del navegador y APIs de terceros.

* **APIs del navegador**: Estas APIs exponen datos del navegador. Como desarrollador web, puedes acceder a estos datos y manipularlos utilizando JavaScript.

* **APIs de terceros**: Estas no están integradas en el navegador de forma predeterminada. Tienes que obtener su código de alguna manera. Normalmente, dispondrán de una documentación detallada que explica cómo utilizar sus servicios. Un ejemplo es la API de Google Maps, que puedes utilizar para mostrar mapas interactivos en tu sitio web.

* **DOM**: DOM significa Document Object Model (Modelo de Objetos del Documento). Es una interfaz de programación que permite interactuar con documentos HTML. Con el DOM, puedes añadir, modificar o eliminar elementos de una página web. La raíz del árbol del DOM es el elemento `html`. Es el contenedor de nivel superior de todo el contenido de un documento HTML. Todos los demás nodos son descendientes de este nodo raíz. Después, por debajo del nodo raíz, encontramos otros nodos en la jerarquía. Un nodo padre es un elemento que contiene otros elementos. Un nodo hijo es un elemento que está contenido dentro de otro elemento.

* **Interfaz `navigator`**: Esta proporciona información sobre el entorno del navegador, como la cadena del agente de usuario, la plataforma y la versión del navegador. Una cadena de agente de usuario es una cadena de texto que identifica el navegador y el sistema operativo que se están utilizando.

* **Interfaz `window`**: Esta representa la ventana del navegador que contiene el documento DOM. Proporciona métodos y propiedades para interactuar con la ventana del navegador, como cambiar su tamaño, abrir nuevas ventanas y navegar a diferentes URL.

## Trabajar con los métodos `querySelector()`, `querySelectorAll()` y `getElementById()`

* **Método `getElementById()`**: Este método se utiliza para obtener un objeto que representa el elemento HTML con el `id` especificado. Recuerda que los `id` deben ser únicos en cada documento HTML, por lo que este método solo devolverá un objeto `Element`.

```html
<div id="container"></div>
<script src="./index.js"></script>
```

```js
const container = document.getElementById("container");
console.log(container)
```

* **Método `querySelector()`**: Este método se utiliza para obtener el primer elemento del documento HTML que coincide con el selector CSS pasado como argumento.

```html
<section class="section"></section>
<script src="./index.js"></script>
```

```js
const section = document.querySelector(".section");
console.log(section)
```

* **Método `querySelectorAll()`**: Puedes utilizar este método para obtener una lista de todos los elementos del DOM que coinciden con un selector CSS específico.

```html
<ul class="ingredients">
  <li>Sugar</li>
  <li>Milk</li>
  <li>Eggs</li>
</ul>
<script src="./index.js"></script>
```

```js
const ingredients = document.querySelectorAll('ul.ingredients li');
console.log(ingredients)
```

## Trabajar con las propiedades `innerText`, `innerHTML`, `createElement()` y `textContent()`

* **Propiedad `innerHTML`**: Esta es una propiedad de `Element` que se utiliza para establecer o actualizar partes del marcado HTML.

```html
<div id="container">
  <!-- Add new elements here -->
</div>
<script src="./index.js"></script>
```

```js
const container = document.getElementById("container");
container.innerHTML = '<ul><li>Cheese</li><li>Tomato</li></ul>';
```

* **Método `createElement`**: Se utiliza para crear un elemento HTML.

```js
const img = document.createElement("img");
```

* **`innerText`**: Representa el contenido de texto visible del elemento HTML y de sus descendientes.

```html
<div id="container">
  <p>Hello, World!</p>
  <p>I'm learning JavaScript</p>
</div>
<script src="./index.js"></script>
```

```js
const container = document.getElementById("container");
console.log(container.innerText);
```

* **`textContent`**: Devuelve el contenido de texto sin formato de un elemento, incluido todo el texto dentro de sus descendientes.

```html
<div id="container">
  <p>Hello, World!</p>
  <p>I'm learning JavaScript</p>
</div>
<script src="./index.js"></script>
```

```js
const container = document.getElementById("container");
console.log(container.textContent);
```

## Trabajar con los métodos `appendChild()` y `removeChild()`

* **Método `appendChild()`**: Este método se utiliza para añadir un nodo al final de la lista de hijos de un nodo padre especificado.

```html
<ul id="desserts">
  <li>Cake</li>
  <li>Pie</li>
</ul>
<script src="./index.js"></script>
```

```js
const dessertsList = document.getElementById("desserts");
const listItem = document.createElement("li");

listItem.textContent = "Cookies";
dessertsList.appendChild(listItem);
```

* **Método `removeChild()`**: Este método se utiliza para eliminar un nodo del DOM.

```html
<section id="example-section">
  <h2>Example sub heading</h2>
  <p>first paragraph</p>
  <p>second paragraph</p>
</section>
<script src="./index.js"></script>
```

```js
const sectionEl = document.getElementById("example-section");
const lastParagraph = document.querySelector("#example-section p:last-of-type");

sectionEl.removeChild(lastParagraph);
```

## Trabajar con el método `setAttribute()`

* **Definición**: Este método se utiliza para establecer el atributo de un elemento determinado. Si el atributo ya existe, su valor se actualiza. De lo contrario, se añade un nuevo atributo con un valor.

```html
<p id="para">I am a paragraph</p>
<script src="./index.js"></script>
```

```js
const para = document.getElementById("para");
para.setAttribute("class", "my-class");
```

## Objeto `Event`

* **Definición**: El objeto `Event` es una carga de datos que se activa cuando un usuario interactúa con tu página web de alguna manera. Estas interacciones pueden ser desde hacer clic en un botón o enfocar un input hasta agitar su dispositivo móvil. Todos los objetos `Event` tendrán la propiedad `type`. Esta propiedad revela el tipo de evento que activó la carga de datos, como `keydown` o `click`. Estos valores corresponden a los mismos valores que puedes pasar a `addEventListener()`, donde puedes capturar y utilizar el objeto `Event`.

## Métodos `addEventListener()` y `removeEventListener()`

* **Método `addEventListener`**: Este método se utiliza para escuchar eventos. Recibe dos argumentos: el evento que quieres escuchar y una función que se llamará cuando ocurra el evento. Algunos ejemplos comunes de eventos serían los eventos de clic, los eventos de entrada y los eventos de cambio.

```html
<button id="btn">Click Me</button>
<script src="./index.js"></script>
```

```js
const btn = document.getElementById("btn");

btn.addEventListener("click", () => alert("You clicked the button"));
```

* **Método `removeEventListener()`**: Este método se utiliza para eliminar un listener de eventos que se añadió previamente a un elemento utilizando el método `addEventListener()`. Esto resulta útil cuando quieres dejar de escuchar un evento concreto en un elemento.

```html
<body>
  <p id="para">Hover over me to disable the button's click event</p>
  <button id="btn">Toggle Background Color</button>
</body>
<script src="./index.js"></script>
```

```js
const bodyEl = document.querySelector("body");
const para = document.getElementById("para");
const btn = document.getElementById("btn");

let isBgColorGrey = true;

function toggleBgColor() {
  bodyEl.style.backgroundColor = isBgColorGrey ? "blue" : "grey";
  isBgColorGrey = !isBgColorGrey;
}

btn.addEventListener("click", toggleBgColor);

para.addEventListener("mouseover", () => {
  btn.removeEventListener("click", toggleBgColor);
});
```

* **Manejadores de eventos inline**: Los manejadores de eventos inline son atributos especiales de un elemento HTML que se utilizan para ejecutar código JavaScript cuando ocurre un evento. En JavaScript moderno, los manejadores de eventos inline no se consideran una buena práctica. Se prefiere utilizar el método `addEventListener`.

```html
<button onclick="alert('Hello World!')">Show alert</button>
```

## El evento `change`

* **Definición**: El evento `change` es un evento especial que se dispara cuando el usuario modifica el valor de determinados elementos de entrada. Algunos ejemplos serían cuando se marca una casilla de verificación o un botón de opción. O cuando el usuario realiza una selección en algo como un selector de fecha o un menú desplegable.

```html
<label>
  Choose a programming language:
  <select class="language" name="language">
    <option value="">---Select One---</option>
    <option value="JavaScript">JavaScript</option>
    <option value="Python">Python</option>
    <option value="C++">C++</option>
  </select>
</label>

<p class="result"></p>
<script src="./index.js"></script>
```

```js
const selectEl = document.querySelector(".language");
const result = document.querySelector(".result");

selectEl.addEventListener("change", (e) => {
  result.textContent = `You enjoy programming in ${e.target.value}.`;
});
```

## Propagación de eventos

* **Definición**: La propagación de eventos, o *event bubbling*, hace referencia a cómo un evento "sube" hacia los objetos padre cuando se activa.

* **Método `stopPropagation()`**: Este método evita que un evento continúe propagándose.

## Delegación de eventos

* **Definición**: La delegación de eventos es el proceso de escuchar eventos que han subido hasta un elemento padre, en lugar de gestionarlos directamente en el elemento que los activó.

## DOMContentLoaded

* **Definición**: El evento `DOMContentLoaded` se dispara cuando todo el documento HTML ha sido cargado y analizado. Si tienes hojas de estilos externas o imágenes, el evento `DOMContentLoaded` no esperará a que estas se carguen. Solo esperará a que se cargue el HTML.

## Trabajar con `style` y `classList`

* **Propiedad `Element.style`**: Esta propiedad es una propiedad de solo lectura que representa el estilo inline de un elemento. Puedes utilizar esta propiedad para obtener o establecer el estilo de un elemento.

```html
<p id="para">This paragraph will turn red.</p>
<script src="./index.js"></script>
```

```js
const paraEl = document.getElementById("para");
paraEl.style.color = "red";
```

* **Propiedad `Element.classList`**: Esta propiedad es una propiedad de solo lectura que puede utilizarse para añadir, eliminar o alternar clases en un elemento.

```html
<link rel="stylesheet" href="./styles.css"/>
<p id="para" class="blue-background">This paragraph will have classes added and removed.</p>
<div id="menu" class="menu">Menu Content</div>
<button id="toggle-btn">Toggle Menu</button>
<script src="./index.js"></script>
```

```css
.highlight {
  background-color: yellow;
}

.blue-background {
  background-color: lightblue;
}

.menu {
  display: none;
  padding: 10px;
  background-color: #f0f0f0;
}

.menu.show {
  display: block;
}
```

```js
// Ejemplo añadiendo una clase
const paraEl = document.getElementById("para");
paraEl.classList.add("highlight");

// Ejemplo eliminando una clase
paraEl.classList.remove("blue-background");

// Ejemplo alternando una clase
const menu = document.getElementById("menu");
const toggleBtn = document.getElementById("toggle-btn");

toggleBtn.addEventListener("click", () => menu.classList.toggle("show"));
```

## Trabajar con los métodos `setTimeout()` y `setInterval()`

* **Método `setTimeout()`**: Este método permite retrasar una acción durante un tiempo determinado.

```js
setTimeout(() => {
 console.log('This runs after 3 seconds'); 
}, 3000);
```

* **Método `setInterval()`**: Este método ejecuta repetidamente un fragmento de código en un intervalo establecido. Como `setInterval()` continúa ejecutando la función proporcionada en el intervalo especificado, es posible que quieras detenerlo. Para ello, tienes que utilizar el método `clearInterval()`.

```js
setInterval(() => {
 console.log('This runs every 2 seconds');
}, 2000);

// Ejemplo utilizando clearInterval
const intervalID = setInterval(() => {
 console.log('This will stop after 5 seconds');
}, 1000);

setTimeout(() => {
 clearInterval(intervalID);
}, 5000);
```

## El método `requestAnimationFrame()`

* **Definición**: Este método permite programar el siguiente paso de tu animación antes del siguiente repintado de pantalla, lo que da como resultado una experiencia fluida y visualmente atractiva. El siguiente repintado de pantalla hace referencia al momento en el que el navegador actualiza la representación visual de la página web. Esto ocurre varias veces por segundo, normalmente unas 60 veces (o 60 fotogramas por segundo) en la mayoría de las pantallas.

```js
function animate() {
 // Update the animation...
 // for example, move an element, change a style, and more.
 update();
 // Request the next frame
 requestAnimationFrame(animate);
}
```

## Web Animations API

* **Definición**: La Web Animations API permite crear y controlar animaciones directamente dentro de JavaScript.

```html
<link rel="stylesheet" href="./styles.css"/>
<div id="square"></div>
<script src="./index.js"></script>
```

```css
#square {
  width: 100px;
  height: 100px;
  background: red;
}
```

```js
const square = document.querySelector('#square');

const animation = square.animate(
 [{ transform: 'translateX(0px)' }, { transform: 'translateX(100px)' }],
 {
   duration: 2000, // hace que la animación dure 2 segundos
   iterations: Infinity, // se repite indefinidamente
   direction: 'alternate', // se mueve de un lado a otro
   easing: 'ease-in-out', // suavizado fluido
 }
);
```

## API Canvas

* **Definición**: La API Canvas es una herramienta potente que permite manipular gráficos directamente dentro de tu archivo JavaScript. Para trabajar con la API Canvas, primero necesitas proporcionar un elemento `canvas` en HTML. Este elemento actúa como una superficie de dibujo que puedes manipular mediante los métodos de instancia y las propiedades de las interfaces de la API Canvas. Esta API cuenta con interfaces como `HTMLCanvasElement`, `CanvasRenderingContext2D`, `CanvasGradient`, `CanvasPattern` y `TextMetrics`, que contienen métodos y propiedades que puedes utilizar para crear gráficos en tu archivo JavaScript.

```html
<canvas id="my-canvas" width="400" height="400"></canvas>
<script src="./index.js"></script>
```

```js
const canvas = document.getElementById('my-canvas');

// Accede al contexto de dibujo del canvas.
// "2d" permite dibujar en dos dimensiones
const ctx = canvas.getContext('2d');

// Establece el color de fondo
ctx.fillStyle = 'crimson';

// Dibuja un rectángulo
ctx.fillRect(1, 1, 150, 100);
```

## Abrir y cerrar diálogos y modales con JavaScript

* **Definiciones de modal y diálogo**: Los diálogos permiten mostrar información o acciones importantes a los usuarios. Con el elemento `dialog` integrado en HTML, puedes crear fácilmente estos diálogos (tanto diálogos modales como no modales) en tus aplicaciones web. Un diálogo modal es un tipo de diálogo que obliga al usuario a interactuar con él antes de poder acceder al resto de la aplicación o página web. En cambio, un diálogo no modal permite al usuario seguir interactuando con otras partes de la página o aplicación incluso cuando el diálogo está abierto. No impide el acceso al resto del contenido.

* **Método `showModal()`**: Este método se utiliza para abrir un modal.

```html
<dialog id="my-modal">
   <p>This is a modal dialog.</p>
</dialog>
<button id="open-modal">Open Modal Dialog</button>
<script src="./index.js"></script>
```

```js
const dialog = document.getElementById('my-modal');
const openButton = document.getElementById('open-modal');

openButton.addEventListener('click', () => {
  dialog.showModal();
});
```

* **Método `close()`**: Este método se utiliza para cerrar el modal.

```html
<dialog id="my-modal">
   <p>This is a modal dialog.</p>
   <button id="close-modal">Close Modal</button>
</dialog>
<button id="open-modal">Open Modal Dialog</button>
<script src="./index.js"></script>
```

```js
const dialog = document.getElementById('my-modal');
const openButton = document.getElementById('open-modal');
const closeButton = document.getElementById('close-modal');

openButton.addEventListener('click', () => {
  dialog.show();
});

closeButton.addEventListener('click', () => {
  dialog.close();
});
```
