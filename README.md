# 📘 JavaScript Notes

Ushbu repoda JavaScript bo‘yicha o‘rganilgan barcha tushunchalar, misollar va kod izohlar bilan to‘plangan. Har bir mavzu alohida bo‘lim ko‘rinishida yoziladi: Classlar, OOP tamoyillari, Module turlari, Functionlar, Array methodlari va hokazo.

---

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
22. [OOP tamoyillari (Encapsulation, Inheritance, Polymorphism, Abstraction)](#22-oop-tamoyillari)

---

2. Class Expression

Description:
Class expression — sinfni qiymat sifatida o‘zgaruvchiga berish yoki boshqa joyga uzatish.

const Car = class {
  constructor(model) {
    this.model = model
  }
}

const myCar = new Car("Tesla")
console.log(myCar.model) // Tesla

3. Constructor

Description:
constructor — classdan obyekt yaratilganda avtomatik ishga tushadigan maxsus metod.

class Book {
  constructor(title, author) {
    this.title = title
    this.author = author
  }
}

const b = new Book("JS Basics", "Jamacoder")
console.log(b.title)  // JS Basics

4. Instance Properties

Description:
Har bir obyektga xos maydonlar.

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

5. Instance Methods

Description:
Instance metodlari — class ichida yozilgan funksiyalar bo‘lib, obyekt orqali chaqiriladi.

class Calculator {
  add(a, b) {
    return a + b // Qo'shish metodi
  }
  multiply(a, b) {
    return a * b // Ko'paytirish metodi
  }
}

const calc = new Calculator()
console.log(calc.add(2, 3))      // 5
console.log(calc.multiply(4, 5)) // 20

6. Static Properties

Description:
Static property — sinfga tegishli, lekin obyektlarga tegishli bo‘lmagan maydon.

class Helper {
  static version = "1.0.0" // Static property
}

console.log(Helper.version) // 1.0.0

7. Static Methods

Description:
Static metodlar class darajasida ishlaydi, obyektlar orqali chaqirilmaydi.

class MathUtils {
  static square(x) {
    return x * x
  }
}

console.log(MathUtils.square(5)) // 25

8. Getters va Setters

Description:
Getter va Setter obyektning propertylarini olish va o‘rnatish uchun ishlatiladi.

class Person {
  constructor(name) {
    this._name = name // private-ish convention
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

9. Inheritance (extends)

Description:
extends orqali class boshqa classdan meros oladi.

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

10. super()

Description:
super() — child class constructorida parent class constructorini chaqirish uchun ishlatiladi.

class Animal {
  constructor(name) {
    this.name = name
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name) // parent constructor chaqirildi
    this.breed = breed
  }
}

const d = new Dog("Buddy", "Labrador")
console.log(d.name)  // Buddy
console.log(d.breed) // Labrador

11. Prototype Inheritance

Description:
JavaScriptda classlar prototip orqali meros oladi.

function Animal(name) {
  this.name = name
}
Animal.prototype.speak = function() {
  console.log(`${this.name} makes a sound`)
}

const dog = new Animal("Rex")
dog.speak() // Rex makes a sound

12. Private Fields

Description:
# bilan belgilangan maydonlar private hisoblanadi, class tashqarisidan ularga kira olmaysiz.

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
// console.log(p.#ssn) // Error

13. Private Methods

Description:
Private metodlar ham # bilan e’lon qilinadi va class tashqarisidan chaqirib bo‘lmaydi.

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
// c.#increment() // Error

14. Protected Fields

Description:
JSda haqiqiy protected yo‘q, lekin _ konvensiyasi orqali protected sifatida ishlatish mumkin.

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

15. Computed Method Names

Description:
Metod nomlarini dynamic ravishda hisoblash mumkin.

const methodName = "sayHello"

class Greeter {
  [methodName]() {
    console.log("Hello!")
  }
}

const g = new Greeter()
g.sayHello() // Hello!

16. new.target

Description:
new.target yordamida function yoki class qaysi contextda chaqirilganini bilish mumkin.

class Person {
  constructor() {
    if (!new.target) {
      throw new Error("Must use new")
    }
    console.log("Created!")
  }
}

const p = new Person() // Created!
// Person() // Error

17. Class Hoisting bo‘lmaydi

Description:
Class declaration hoisting qilinmaydi, ya’ni classdan oldin unga murojaat qila olmaysiz.

// console.log(Person) // Error
class Person {}

18. Abstract Class (imitatsiya)

Description:
JSda abstract class yo‘q, lekin new.target bilan imitasiya qilinadi.

class AbstractAnimal {
  constructor() {
    if (new.target === AbstractAnimal) {
      throw new Error("Cannot instantiate AbstractAnimal directly")
    }
  }
}

class Dog extends AbstractAnimal {}
const d = new Dog() // OK
// const a = new AbstractAnimal() // Error

19. Mixins

Description:
Mixin — bir nechta classlar yoki funksional metodlarni birlashtirish usuli.

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

20. instanceof

Description:
instanceof operatori obyekt qaysi classdan yaratilganini tekshiradi.

class Person {}
const p = new Person()
console.log(p instanceof Person) // true
console.log(p instanceof Object) // true

21. this

Description:
this — hozirgi kontekstdagi obyektga ishora qiladi. Class ichida obyektga murojaat qiladi.

class Person {
  constructor(name) {
    this.name = name
  }
  sayName() {
    console.log(this.name)
  }
}

const p = new Person("Ali")
p.sayName() // Ali

22. OOP tamoyillari

Description:

Encapsulation — obyekt ichidagi data va metodlarni bir joyda saqlash

Inheritance — classlar orasida meros olish

Polymorphism — bir xil interfeys orqali turli implementatsiyalar

Abstraction — murakkab tizimni soddalashtirish

class Animal {
  speak() { console.log("Animal speaks") }
}

class Dog extends Animal {
  speak() { console.log("Dog barks") }
}

const a = new Animal()
const d = new Dog()

a.speak() // Animal speaks
d.speak() // Dog barks
