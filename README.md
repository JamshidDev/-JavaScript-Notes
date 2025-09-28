# Class Declaration

**Description:**
Class deklaratsiyasi — yangi sinf (class) yaratishning oddiy yo‘li. Bu `class` kalit so‘zi bilan yoziladi va nomlanadi. Sinf odatda obyekt yaratish uchun qolip (shablon) hisoblanadi.

**Example code:**

```js
// Oddiy class e'lon qilish
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

// Classdan obyekt yaratish
const user = new Person("Ali", 25)
console.log(user.name) // Ali
```

---

# Class Expression

**Description:**
Class expression — sinfni o‘zgaruvchiga yoki boshqa joyga qiymat sifatida berish. Bunda classga nom berish shart emas (anonim bo‘lishi ham mumkin).

**Example code:**

```js
// Anonim class expression
const Car = class {
  constructor(model) {
    this.model = model
  }
}

const myCar = new Car("Tesla")
console.log(myCar.model) // Tesla

// Nomlangan class expression
const Animal = class AnimalClass {
  constructor(type) {
    this.type = type
  }
}
console.log(new Animal("Dog").type) // Dog
```

---

# Constructor

**Description:**
`constructor` — bu maxsus metod bo‘lib, classdan obyekt yaratilganda avtomatik ishlaydi. Unda odatda boshlang‘ich qiymatlar (`properties`) beriladi.

**Example code:**

```js
class Book {
  constructor(title, author) {
    // constructor chaqirilganda shu ishlaydi
    this.title = title
    this.author = author
  }
}

const b = new Book("JavaScript Basics", "Jamacoder")
console.log(b.title)  // JavaScript Basics
```

---

# Instance Properties

**Description:**
Instance properties — classdan yaratilgan har bir obyektga xos bo‘lgan maydonlar (property). Ular `this` orqali belgilanadi.

**Example code:**

```js
class User {
  constructor(name, age) {
    this.name = name  // instance property
    this.age = age    // instance property
  }
}

const u1 = new User("Hasan", 20)
const u2 = new User("Husan", 22)

console.log(u1.name) // Hasan
console.log(u2.name) // Husan
```

---

# Instance Methods

**Description:**
Instance metodlari — bu class ichida yozilgan funksiyalar bo‘lib, obyektlar orqali chaqiriladi.

**Example code:**

```js
class Calculator {
  add(a, b) {
    return a + b
  }
  multiply(a, b) {
    return a * b
  }
}

const calc = new Calculator()
console.log(calc.add(2, 3))      // 5
console.log(calc.multiply(4, 5)) // 20
```
