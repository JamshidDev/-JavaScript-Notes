
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

