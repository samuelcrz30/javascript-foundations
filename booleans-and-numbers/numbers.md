## Comparaciones y los tipos de datos `null` y `undefined`

* **Comparaciones y `undefined`**: Una variable es `undefined` cuando ha sido declarada pero no se le ha asignado un valor. Es el valor predeterminado de las variables no inicializadas y de los parámetros de funciones a los que no se les proporcionó un argumento. `undefined` se convierte en `NaN` en contextos numéricos, lo que hace que todas las comparaciones numéricas con `undefined` devuelvan `false`.

```js
console.log(undefined < 0); // false (NaN < 0 es false)
console.log(undefined >= 0); // false (NaN >= 0 es false)
```

* **Comparaciones y `null`**: El tipo `null` representa la ausencia intencional de un valor. `null` se convierte en `0` en contextos numéricos, lo que puede producir comportamientos inesperados en las comparaciones numéricas:

```js
console.log(null < 0); // false (0 < 0 es false)
console.log(null >= 0); // true (0 >= 0 es true)
```

* Al utilizar el operador de igualdad (`==`), `null` y `undefined` solo son iguales entre sí y consigo mismos:

```js
console.log(null == undefined); // true
console.log(null == 0); // false
console.log(undefined == NaN); // false
```

* Sin embargo, al utilizar el operador de igualdad estricta (`===`), que comprueba tanto el valor como el tipo sin realizar coerción de tipos, `null` y `undefined` no son iguales:

```js
console.log(null === undefined); // false
```

## Sentencias `switch`

* **Definición**: Una sentencia `switch` evalúa una expresión y compara su valor con una serie de cláusulas `case`. Cuando se encuentra una coincidencia, se ejecuta el bloque de código asociado a ese `case`. Se debe colocar una sentencia `break` al final de cada `case` para terminar su ejecución y continuar con el siguiente. El `case default` es opcional y solo se ejecuta si ninguno de los otros casos coincide. El `case default` se coloca al final de una sentencia `switch`.

```js
const dayOfWeek = 3; 

switch (dayOfWeek) {
  case 1:
    console.log("It's Monday! Time to start the week strong.");
    break;
  case 2:
    console.log("It's Tuesday! Keep the momentum going.");
    break;
  case 3:
    console.log("It's Wednesday! We're halfway there.");
    break;
  case 4:
    console.log("It's Thursday! Almost the weekend.");
    break;
  case 5:
    console.log("It's Friday! The weekend is near.");
    break;
  case 6:
    console.log("It's Saturday! Enjoy your weekend.");
    break;
  case 7:
    console.log("It's Sunday! Rest and recharge.");
    break;
  default:
    console.log("Invalid day! Please enter a number between 1 and 7.");
}
```
