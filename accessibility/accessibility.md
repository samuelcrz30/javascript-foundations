# Repaso de JavaScript y accesibilidad

## Atributos comunes de accesibilidad ARIA

* **Atributo `aria-expanded`**: Se utiliza para comunicar el estado de una función de alternancia (o divulgación) a los usuarios de lectores de pantalla.

```html
<button id="menuBtn" aria-expanded="false">Menu</button>

<script>
  const btn = document.getElementById("menuBtn");

  btn.addEventListener("click", () => {
    const expanded = btn.getAttribute("aria-expanded") === "true";
    btn.setAttribute("aria-expanded", String(!expanded));
  });
</script>

```

* **Atributo `aria-haspopup`**: Este estado se utiliza para indicar que un elemento interactivo activará un elemento emergente cuando se active. Solo puedes utilizar el atributo `aria-haspopup` cuando el elemento emergente tenga uno de los siguientes roles: `menu`, `listbox`, `tree`, `grid` o `dialog`. El valor de `aria-haspopup` debe ser uno de estos roles o `true`, que es equivalente a `menu`.

```html
<button
  id="menubutton"
  aria-haspopup="menu"
  aria-controls="filemenu"
  aria-expanded="false"
>
  File
</button>

<ul
  id="filemenu"
  role="menu"
  aria-labelledby="menubutton"
  hidden
>
  <li role="menuitem" tabindex="-1">Open</li>
  <li role="menuitem" tabindex="-1">New</li>
  <li role="menuitem" tabindex="-1">Save</li>
  <li role="menuitem" tabindex="-1">Delete</li>
</ul>

<script>
  const button = document.getElementById("menubutton");
  const menu = document.getElementById("filemenu");

  button.addEventListener("click", () => {
    const expanded = button.getAttribute("aria-expanded") === "true";

    button.setAttribute("aria-expanded", String(!expanded));
    menu.hidden = expanded;
  });
</script>

```

* **Atributo `aria-checked`**: Este atributo se utiliza para indicar si un elemento está en estado marcado. Se utiliza principalmente al crear casillas de verificación, botones de opción, interruptores y listboxes personalizados.

```html
<div
  id="checkbox"
  role="checkbox"
  aria-checked="true"
  tabindex="0"
  style="
    display: inline-flex;
    align-items: center;
    gap: 6px;
    cursor: pointer;
  "
>
  <span
    id="box"
    aria-hidden="true"
    style="
      width: 16px;
      height: 16px;
      border: 2px solid blue;
      background: blue;
      display: inline-block;
    "
  ></span>
  Checkbox
</div>

<script>
  const checkbox = document.getElementById("checkbox");
  const box = document.getElementById("box");

  const toggle = () => {
    const checked = checkbox.getAttribute("aria-checked") === "true";
    checkbox.setAttribute("aria-checked", String(!checked));
    box.style.background = checked ? "white" : "black";
  };

  checkbox.addEventListener("click", toggle);

  checkbox.addEventListener("keydown", (e) => {
    if (e.key === " " || e.key === "Enter") {
      e.preventDefault();
      toggle();
    }
  });
</script>

```

* **Atributo `aria-disabled`**: Este estado se utiliza para indicar que un elemento está deshabilitado únicamente para las personas que utilizan tecnologías de asistencia, como los lectores de pantalla.

```html
<div
  id="editBtn"
  role="button"
  tabindex="-1"
  aria-disabled="true"
  style="opacity: 0.5; cursor: not-allowed;"
>
  Edit
</div>

<button id="toggle">Toggle Disabled</button>

<script>
  const editBtn = document.getElementById("editBtn");
  const toggleBtn = document.getElementById("toggle");

  toggleBtn.addEventListener("click", () => {
    const disabled = editBtn.getAttribute("aria-disabled") === "true";

    editBtn.setAttribute("aria-disabled", String(!disabled));
    editBtn.tabIndex = disabled ? 0 : -1;
    editBtn.style.opacity = disabled ? "1" : "0.5";
    editBtn.style.cursor = disabled ? "pointer" : "not-allowed";
  });
</script>

```

* **Atributo `aria-selected`**: Este estado se utiliza para indicar que un elemento está seleccionado. Puedes utilizar este estado en controles personalizados, como una interfaz con pestañas, un listbox o una cuadrícula.

```html
<div role="tablist">
  <button role="tab" aria-selected="true">Tab 1</button>
  <button role="tab" aria-selected="false">Tab 2</button>
  <button role="tab" aria-selected="false">Tab 3</button>
</div>

<script>
  const tabs = document.querySelectorAll('[role="tab"]');

  tabs.forEach((tab) => {
    tab.addEventListener("click", () => {
      tabs.forEach(t => t.setAttribute("aria-selected", "false"));
      tab.setAttribute("aria-selected", "true");
    });
  });
</script>

```

* **Atributo `aria-controls`**: Se utiliza para asociar un elemento con otro elemento que controla. Esto ayuda a las personas que utilizan tecnologías de asistencia a comprender la relación entre los elementos.

```html
<div role="tablist">
  <button 
    role="tab"
    id="tab1"
    aria-controls="section1"
    aria-selected="true"
  >
    Tab 1
  </button>
  <button
    role="tab"
    id="tab2"
    aria-controls="section2"
    aria-selected="false"
  >
    Tab 2
  </button>
  <button
    role="tab"
    id="tab3"
    aria-controls="section3"
    aria-selected="false"
  >
    Tab 3
  </button>
</div>

```

* **Atributo `hidden`**: Oculta los paneles inactivos tanto para los usuarios visuales como para los usuarios de tecnologías de asistencia.

## Trabajar con regiones activas y contenido dinámico

* **Atributo `aria-live`**: Convierte parte de una página web en una región activa, lo que significa que cualquier actualización dentro de esa área será anunciada por un lector de pantalla para que los usuarios no se pierdan cambios importantes.
* **Valor `polite`**: La mayoría de las regiones activas utilizan este valor. Este valor significa que la actualización no es urgente, por lo que el lector de pantalla puede esperar hasta terminar cualquier anuncio actual o hasta que el usuario complete su acción actual antes de anunciar la actualización.

Aquí tienes un ejemplo de una región activa que se actualiza dinámicamente mediante JavaScript:

```html
<div aria-live="polite" id="status"></div>

<button id="updateStatus">Update Status</button>

<script>
  const statusEl = document.getElementById("status");
  const btn = document.getElementById("updateStatus");

  btn.addEventListener("click", () => {
    statusEl.textContent = "Your file has been successfully uploaded.";
  });
</script>

```

* **Atributo `contenteditable`**: Convierte el elemento en un editor activo, permitiendo a los usuarios actualizar su contenido como si fuera un campo de texto. Cuando no haya una etiqueta o encabezado visible para una región `contenteditable`, añade un nombre accesible utilizando el atributo `aria-label` para ayudar a los usuarios de lectores de pantalla a comprender el propósito del área editable.

```html
<div
  contenteditable="true"
  aria-label="Note editor"
  id="editor"
  style="border: 1px solid #ccc; padding: 8px;"
>
  Editable content goes here
</div>

<p id="status" aria-live="polite"></p>

<script>
  const editor = document.getElementById("editor");
  const status = document.getElementById("status");

  editor.addEventListener("input", () => {
    status.textContent = "Content updated";
  });
</script>

```

## Eventos `focus` y `blur`

* **Evento `blur`**: Se ejecuta cuando un elemento pierde el foco.

```html
<input
  id="nameInput"
  type="text"
  placeholder="Type here and click outside"
  aria-label="Name input"
/>

<p id="status" aria-live="polite"></p>

<script>
  const input = document.getElementById("nameInput");
  const status = document.getElementById("status");

  input.addEventListener("blur", () => {
    status.textContent = "Input lost focus";
  });
</script>

```

* **Evento `focus`**: Se ejecuta cuando un elemento recibe el foco.

```html
<input
  id="emailInput"
  type="email"
  placeholder="Click or tab into this field"
  aria-label="Email input"
/>

<p id="status" aria-live="polite"></p>

<script>
  const input = document.getElementById("emailInput");
  const status = document.getElementById("status");

  input.addEventListener("focus", () => {
    status.textContent = "Input received focus";
  });
</script>
```
