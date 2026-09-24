# Repaso de las clases de JavaScript

## Conceptos básicos sobre el trabajo con clases

* **Definición**: Las clases en JavaScript se utilizan para definir plantillas para crear objetos y encapsular datos. Las clases incluyen un constructor, que es un método especial que se ejecuta automáticamente cuando se crea un nuevo objeto a partir de la clase. Se utiliza para inicializar las propiedades del objeto. La palabra clave `this` se utiliza aquí para hacer referencia a la instancia actual de la clase. Debajo del constructor, puedes tener lo que se denominan métodos. Los métodos son funciones definidas dentro de una clase que realizan acciones u operaciones sobre los datos o el estado de la clase. Se utilizan para definir comportamientos que las instancias de la clase pueden realizar.

```js
class Dog {
  constructor(name) {
    this.name = name;
  }

  bark() {
    console.log(`${this.name} says woof!`);
  }
}

const dog = new Dog("Gino");
console.log(dog.name);  // Gino

```

Para crear una nueva instancia de la clase, utilizarás la palabra clave `new` seguida del nombre de la clase:

```js
const dog = new Dog("Gino");

```

También puedes crear clases como expresiones de clase. Esto ocurre cuando la clase es anónima y se asigna a una variable.

```js
const Dog = class {
  constructor(name) {
    this.name = name;
  }

  bark() {
    console.log(`${this.name} says woof!`);
  }
};

const dog = new Dog("Gino");
console.log(dog.name);  // Gino
dog.bark();  // Gino says woof!

```

## Herencia de clases

* **Definición**: En programación, la herencia permite definir clases que heredan propiedades y métodos de clases padre. Esto favorece la reutilización de código y establece una relación jerárquica entre las clases. Una clase padre es una clase que actúa como una plantilla para otras clases. Define propiedades y métodos que son heredados por otras clases. Una clase hija es una clase que hereda las propiedades y métodos de otra clase. Las clases hijas también pueden ampliar la funcionalidad de sus clases padre añadiendo nuevas propiedades y métodos. En JavaScript, utilizamos la palabra clave `extends` para implementar la herencia. Esta palabra clave indica que una clase es la clase hija de otra clase.

```js
class Vehicle {
  constructor(brand, year) {
    this.brand = brand;
    this.year = year;
  }
}

class Car extends Vehicle {
  honk() {
    console.log("Honk! Honk!");
  }
}

const myCar = new Car("freeCodeCamp Motors", 2019);
console.log(myCar.brand);  // freeCodeCamp Motors
console.log(myCar.year);  // 2019
myCar.honk();  // Honk! Honk!

```

La palabra clave `super` se utiliza para acceder a los métodos, constructores y campos de la clase padre.

```js
class Vehicle {
  constructor(brand, year) {
    this.brand = brand;
    this.year = year;
  }
}

class Car extends Vehicle {
  constructor(brand, year, numDoors) {
    super(brand, year);
    this.numDoors = numDoors;
  }
}

const myCar = new Car("freeCodeCamp Motors", 2019, 4);
console.log(myCar.brand);  // freeCodeCamp Motors
console.log(myCar.year);  // 2019
console.log(myCar.numDoors);  // 4

```

## Trabajando con métodos estáticos y propiedades estáticas

* **Métodos estáticos**: Estos métodos se utilizan a menudo para funciones de utilidad que no necesitan acceder al estado específico de un objeto. Se definen dentro de las clases para encapsular funcionalidades relacionadas.

```js
class Movie {
  constructor(title, rating) {
    this.title = title;
    this.rating = rating;
  }

  static compareMovies(movieA, movieB) {
    if (movieA.rating > movieB.rating) {
      console.log(`${movieA.title} has a higher rating.`);
    } else if (movieA.rating < movieB.rating) {
      console.log(`${movieB.title} has a higher rating.`);
    } else {
      console.log("These movies have the same rating.");
    }
  }
}

let movieA = new Movie("Movie A", 80);
let movieB = new Movie("Movie B", 45);

Movie.compareMovies(movieA, movieB);  // Movie A has a higher rating.

```

Los métodos estáticos también son útiles para implementar métodos "factory". Un método factory es un método que defines además del constructor para crear objetos basándose en criterios específicos.

```js
class Pizza {
  constructor(type, price) {
    this.type = type;
    this.price = price;
  }

  static createMargherita() {
    return new this("Margherita", 6.99);
  }
}

let myPizza = Pizza.createMargherita();
console.log(myPizza);  // Pizza { type: "Margherita", price: 6.99 }
console.log(myPizza.type);  // Margherita

```

* **Propiedades estáticas**: Estas propiedades se utilizan para definir valores o atributos que están asociados a la propia clase, en lugar de a las instancias de la clase. Las propiedades estáticas se comparten entre todas las instancias de la clase y se puede acceder a ellas sin crear una instancia de la clase.

```ts
class Car {
  // Propiedad estática
  static numberOfWheels = 4;

  constructor(make, model) {
    this.make = make;
    this.model = model;
  }

  // Método de instancia
  getCarInfo() {
    return `${this.make} ${this.model}`;
  }

  // Método estático
  static getNumberOfWheels() {
    return Car.numberOfWheels;
  }
}

// Accediendo directamente a la propiedad estática desde la clase
console.log(Car.numberOfWheels);  // 4
```
