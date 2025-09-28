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

## 1. Class Declaration

**Description:**  
Class deklaratsiyasi yangi sinfni yaratishning asosiy usuli.  

```js
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

const user = new Person("Ali", 25)
console.log(user.name) // Ali

##2. Class Expression

Description:
Class expression — sinfni qiymat sifatida o‘zgaruvchiga berish yoki boshqa joyga uzatish.

```js
const Car = class {
  constructor(model) {
    this.model = model
  }
}

const myCar = new Car("Tesla")
console.log(myCar.model) // Tesla

##3. Constructor

Description:
constructor — classdan obyekt yaratilganda avtomatik ishga tushadigan maxsus metod.

```js
class Book {
  constructor(title, author) {
    this.title = title
    this.author = author
  }
}

const b = new Book("JS Basics", "Jamacoder")
console.log(b.title)  // JS Basics

