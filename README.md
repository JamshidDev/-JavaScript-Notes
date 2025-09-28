
## 📑 Mundarija

1. [Class Declaration](#1-class-declaration)  
2. [Class Expression](#2-class-expression)  
3. [Constructor](#3-constructor)  
4. [Instance Properties](#4-instance-properties)  
5. [Instance Methods](#5-instance-methods)  
6. [Static Properties](#6-static-properties)  
7. [Static Methods](#7-static-methods)  
8. [Getters va Setters](#8-getters-va-setters)  
9. [Inheritance (extends)](#9-inheritance-extends)  
10. [super()](#10-super)  
11. [Prototype Inheritance](#11-prototype-inheritance)  
12. [Private Fields](#12-private-fields)  
13. [Private Methods](#13-private-methods)  
14. [Protected Fields](#14-protected-fields)  
15. [Computed Method Names](#15-computed-method-names)  
16. [new.target](#16-newtarget)  
17. [Class Hoisting bo‘lmaydi](#17-class-hoisting-bolmaydi)  
18. [Abstract Class (imitatsiya)](#18-abstract-class-imitatsiya)  
19. [Mixins](#19-mixins)  
20. [instanceof](#20-instanceof)  
21. [this](#21-this)  
22. [OOP tamoyillari](#22-oop-tamoyillari)

---

## 1. Class Declaration

**Class deklaratsiyasi — JavaScriptda yangi sinf yaratishning standart usuli. `class` kalit so‘zi bilan e’lon qilinadi va odatda nomlanadi. Shu sinfdan obyektlar yaratish mumkin.**

```js
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

const user = new Person("Ali", 25)
console.log(user.name) // Ali
```

## 2. Class Expression

**Class expression — sinfni qiymat sifatida o‘zgaruvchiga berish yoki boshqa joyga uzatish uchun ishlatiladi. U anonim yoki nomlangan bo‘lishi mumkin.**

```js
// Anonim class
const Car = class {
  constructor(model) {
    this.model = model
  }
}

const myCar = new Car("Tesla")
console.log(myCar.model) // Tesla
```

## 3. Constructor

**constructor — classdan obyekt yaratilganda avtomatik ishga tushadigan maxsus metod. Unda obyektning boshlang‘ich qiymatlari belgilanadi.**

```js
class Book {
  constructor(title, author) {
    this.title = title
    this.author = author
  }
}

const b = new Book("JS Basics", "Jamacoder")
console.log(b.title)  // JS Basics
```

## 4. Instance Properties

**Instance properties — bu obyektga tegishli maydonlar. Har bir obyekt o‘ziga xos qiymatga ega bo‘ladi.**

```js
class User {
  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

const u1 = new User("Hasan", 20)
const u2 = new User("Husan", 22)

console.log(u1.name) // Hasan
console.log(u2.name) // Husan
```

## 5. Instance Methods

**Instance metodlari — class ichida yozilgan funksiyalar bo‘lib, faqat obyekt orqali chaqiriladi. Ular obyektning ma’lumotlariga ishlov beradi.**

```js
class Calculator {
  add(a, b) {
    return a + b // Qo'shish
  }
  multiply(a, b) {
    return a * b // Ko'paytirish
  }
}

const calc = new Calculator()
console.log(calc.add(2, 3))      // 5
console.log(calc.multiply(4, 5)) // 20
```

## 6. Static Properties

**Static property — bu sinfga tegishli maydon, lekin obyektlarga tegishli emas. static kalit so‘zi bilan e’lon qilinadi.**

```js
class Helper {
  static version = "1.0.0"
}

console.log(Helper.version) // 1.0.0
```

## 7. Static Methods

**Static metodlar class darajasida ishlaydi va obyektlar orqali chaqirilmaydi. Ular utility funksiyalar uchun qulay.**

```js
class MathUtils {
  static square(x) {
    return x * x
  }
}

console.log(MathUtils.square(5)) // 25
```

## 8. Getters va Setters

**Getter va Setter obyektning propertylarini olish va o‘rnatish uchun ishlatiladi. Ular propertyni private yoki encapsulated qilishda foydali.**

```js
class Person {
  constructor(name) {
    this._name = name
  }

  get name() {
    return this._name
  }

  set name(newName) {
    this._name = newName
  }
}

const p = new Person("Ali")
console.log(p.name) // Ali
p.name = "Hasan"
console.log(p.name) // Hasan
```

## 9. Inheritance (extends)

**Inheritance — bu bir classning boshqa classdan meros olish imkoniyati. Child class parent class metodlari va propertylarini ishlata oladi.**

```js
class Animal {
  constructor(name) {
    this.name = name
  }
  speak() {
    console.log(`${this.name} makes a sound`)
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks`)
  }
}

const d = new Dog("Buddy")
d.speak() // Buddy barks
```

## 10. super()

**super() — child class constructorida parent class constructorini chaqirish uchun ishlatiladi. Shu orqali parent propertylarini o‘rnatish mumkin.**

```js
class Animal {
  constructor(name) {
    this.name = name
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name)
    this.breed = breed
  }
}

const d = new Dog("Buddy", "Labrador")
console.log(d.name)  // Buddy
console.log(d.breed) // Labrador
```

## 11. Prototype Inheritance

**JavaScriptda classlar prototip orqali meros oladi. Har bir obyekt [[Prototype]] orqali parentning property va metodlariga kiradi.**

```js
function Animal(name) {
  this.name = name
}
Animal.prototype.speak = function() {
  console.log(`${this.name} makes a sound`)
}

const dog = new Animal("Rex")
dog.speak() // Rex makes a sound

12. Private Fields

# bilan e’lon qilingan maydonlar private hisoblanadi va class tashqarisidan ularga kira olmaysiz. Bu encapsulation uchun qulay.

class Person {
  #ssn
  constructor(name, ssn) {
    this.name = name
    this.#ssn = ssn
  }

  getSSN() {
    return this.#ssn
  }
}

const p = new Person("Ali", "123-45-6789")
console.log(p.getSSN()) // 123-45-6789
```

## 13. Private Methods

**Private metodlar ham # bilan e’lon qilinadi va faqat class ichida ishlaydi. Class tashqarisidan chaqirib bo‘lmaydi.**

```js
class Counter {
  #count = 0
  #increment() {
    this.#count++
  }

  increase() {
    this.#increment()
    return this.#count
  }
}

const c = new Counter()
console.log(c.increase()) // 1
```

## 14. Protected Fields

**JavaScriptda haqiqiy protected yo‘q, lekin _ bilan belgilangan propertylar child classlar tomonidan ishlatilishi mumkin.**

```js
class Person {
  _name
  constructor(name) {
    this._name = name
  }
}

class Employee extends Person {
  getName() {
    return this._name
  }
}

const e = new Employee("Ali")
console.log(e.getName()) // Ali
```

## 15. Computed Method Names

**Metod nomlarini dynamic ravishda [expression] bilan hisoblash mumkin. Bu flexibility beradi.**

```js
const methodName = "sayHello"

class Greeter {
  [methodName]() {
    console.log("Hello!")
  }
}

const g = new Greeter()
g.sayHello() // Hello!
```

## 16. new.target

**new.target yordamida class yoki function qaysi kontekstda chaqirilganini bilish mumkin. Shu orqali abstract class imitatsiya qilish mumkin.**

```js
class Person {
  constructor() {
    if (!new.target) {
      throw new Error("Must use new")
    }
    console.log("Created!")
  }
}

const p = new Person() // Created!
```

## 17. Class Hoisting bo‘lmaydi

**Class declaration hoisting qilinmaydi. Shu sababdan classdan oldin unga murojaat qilish mumkin emas.**

```js
// console.log(Person) // Error
class Person {}

18. Abstract Class (imitatsiya)

JSda abstract class yo‘q, lekin new.target bilan uni imitasiya qilish mumkin.

class AbstractAnimal {
  constructor() {
    if (new.target === AbstractAnimal) {
      throw new Error("Cannot instantiate AbstractAnimal directly")
    }
  }
}

class Dog extends AbstractAnimal {}
const d = new Dog() // OK
```

## 19. Mixins

**Mixin — bir nechta classlar yoki funksional metodlarni birlashtirish usuli.**

```js
let sayHiMixin = {
  sayHi() {
    console.log(`Hi ${this.name}`)
  }
}

class User {
  constructor(name) {
    this.name = name
  }
}

Object.assign(User.prototype, sayHiMixin)

new User("Ali").sayHi() // Hi Ali
```

## 20. instanceof

**instanceof operatori obyekt qaysi classdan yaratilganini tekshiradi.**

```js
class Person {}
const p = new Person()
console.log(p instanceof Person) // true
console.log(p instanceof Object) // true
```
