# JavaScript Modules - Complete Guide
## 1. Named Export
**Moduldan bir nechta qiymat, funksiya yoki klasslarni eksport qilish uchun ishlatiladi. Har bir eksport qilingan element o'z nomi bilan identifikatsiya qilinadi va import qilishda aynan shu nomdan foydalaniladi.**

```js
javascript// math.js

// Har bir element oldiga export yozish
export const PI = 3.14159;

export function add(a, b) {
  return a + b;
}

export function multiply(a, b) {
  return a * b;
}

// Yoki fayl oxirida birgalikda eksport qilish
const subtract = (a, b) => a - b;
const divide = (a, b) => a / b;

export { subtract, divide };
```

## 2. Named Export with Rename

**Eksport qilayotganda element nomini o'zgartirish imkonini beradi. Bu nom to'qnashuvi yoki moduldan foydalanuvchilar uchun aniqroq nomlar berish uchun foydali.**

```js
javascript// shapes.js

function calculateArea(radius) {
  return Math.PI * radius * radius;
}

function calculatePerimeter(radius) {
  return 2 * Math.PI * radius;
}

// Eksport qilishda nomlarni o'zgartirish
export { 
  calculateArea as circleArea,
  calculatePerimeter as circlePerimeter 
};
```

## 3. Default Export

**Har bir modulda faqat bitta default eksport bo'lishi mumkin. Bu modulning asosiy funksiyasi yoki klassi bo'lib, import qilishda istalgan nom berilishi mumkin.**

```js
javascript// logger.js

// Funksiyani to'g'ridan-to'g'ri default eksport qilish
export default function log(message) {
  console.log(`[LOG]: ${message}`);
}

// Yoki avval e'lon qilib keyin eksport qilish
function Logger(prefix) {
  this.prefix = prefix;
}

export default Logger;
```

## 4. Default Export (Class)

**Klasslarni default eksport qilish - obyekt yo'naltirilgan dasturlashda keng tarqalgan usul.**

```js
javascript// User.js

export default class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  // Metodlar
  getInfo() {
    return `${this.name} (${this.email})`;
  }

  // Static metod
  static createGuest() {
    return new User('Guest', 'guest@example.com');
  }
}
```

## 5. Named Import

**Named eksportlarni import qilish uchun jingalak qavslar ishlatiladi va eksport qilingan aniq nomlar ko'rsatiladi.**

```js
javascript// app.js

// Bir nechta elementni import qilish
import { PI, add, multiply } from './math.js';

console.log(PI); // 3.14159
console.log(add(5, 3)); // 8
console.log(multiply(4, 2)); // 8

// Faqat kerakli elementlarni import qilish
import { subtract } from './math.js';
console.log(subtract(10, 3)); // 7
```

## 6. Named Import with Rename

**Import qilayotganda element nomini o'zgartirish. Bu nom to'qnashuvi yoki kodda aniqroq nomlar ishlatish uchun foydali.**

```js
javascript// app.js

// Import qilishda nomlarni o'zgartirish
import { 
  circleArea as getCircleArea,
  circlePerimeter as getCirclePerimeter 
} from './shapes.js';

console.log(getCircleArea(5)); // 78.53975
console.log(getCirclePerimeter(5)); // 31.4159
```

## 7. Default Import
**Default eksportni import qilish. Jingalak qavslar ishlatilmaydi va istalgan nom berilishi mumkin.**

```js
javascript// app.js

// Default eksportni import qilish
import log from './logger.js';

log('Application started'); // [LOG]: Application started

// Klass uchun
import User from './User.js';

const user = new User('Ali', 'ali@example.com');
console.log(user.getInfo()); // Ali (ali@example.com)
```


## 8. Mixed Import (Default + Named)

** Bir moduldan ham default, ham named eksportlarni birga import qilish mumkin.**

```js
javascript// utils.js
export default function formatDate(date) {
  return date.toISOString();
}

export const VERSION = '1.0.0';
export function capitalize(str) {
  return str.charAt(0).toUpperCase() + str.slice(1);
}

// app.js
// Default va named importlarni birga ishlatish
import formatDate, { VERSION, capitalize } from './utils.js';

console.log(formatDate(new Date())); // 2024-01-15T10:30:00.000Z
console.log(VERSION); // 1.0.0
console.log(capitalize('hello')); // Hello
```

## 9. Namespace Import

**Modulning barcha eksportlarini bitta obyekt ichida import qilish. Bu kodni tashkillashtirish va nom to'qnashuvlarini oldini olish uchun juda foydali.**

```js
javascript// math.js
export const PI = 3.14159;
export function add(a, b) { return a + b; }
export function multiply(a, b) { return a * b; }

// app.js
// Barcha eksportlarni bitta obyekt sifatida olish
import * as Math from './math.js';

console.log(Math.PI); // 3.14159
console.log(Math.add(5, 3)); // 8
console.log(Math.multiply(4, 2)); // 8

// Har bir funksiya Math.functionName orqali chaqiriladi
```

## 10. Re-export

**Boshqa modullardan import qilgan elementlarni darhol qayta eksport qilish. Bu modullarni birlashtirish va tashkillashtirish uchun ishlatiladi.**

```js
javascript// shapes/circle.js
export function circleArea(r) { return Math.PI * r * r; }

// shapes/square.js
export function squareArea(side) { return side * side; }

// shapes/triangle.js
export function triangleArea(base, height) { return (base * height) / 2; }

// shapes/index.js
// Barcha shakllarni bir joydan eksport qilish
export { circleArea } from './circle.js';
export { squareArea } from './square.js';
export { triangleArea } from './triangle.js';

// app.js
// Endi barcha shakllarni bir joydan import qilish mumkin
import { circleArea, squareArea, triangleArea } from './shapes/index.js';
```

## 11. Re-export All

**Modulning barcha eksportlarini boshqa modul orqali qayta eksport qilish.**

```js
javascript// components/Button.js
export class Button { }

// components/Input.js
export class Input { }

// components/Form.js
export class Form { }

// components/index.js
// Barcha komponentlarni qayta eksport qilish
export * from './Button.js';
export * from './Input.js';
export * from './Form.js';

// app.js
// Hamma narsani bir marta import qilish
import { Button, Input, Form } from './components/index.js';
```

## 12. Re-export with Rename

**Qayta eksport qilayotganda elementlarning nomini o'zgartirish.**

```js
javascript// api/users.js
export function fetchUsers() { /* ... */ }

// api/posts.js
export function fetchPosts() { /* ... */ }

// api/index.js
// Nomlarni o'zgartirib qayta eksport qilish
export { fetchUsers as getUsers } from './users.js';
export { fetchPosts as getPosts } from './posts.js';

// app.js
import { getUsers, getPosts } from './api/index.js';
```

## 13. Side Effect Import

**Modul kodini bajarish uchun import qilish, lekin hech narsa olmaslik. Bu global sozlamalar, polyfilllar yoki CSS yuklash uchun ishlatiladi.**

```js
javascript// polyfills.js
// Array.prototype.at() metodini qo'shish
if (!Array.prototype.at) {
  Array.prototype.at = function(index) {
    if (index < 0) index = this.length + index;
    return this[index];
  };
}

// app.js
// Faqat polyfillni yuklash uchun
import './polyfills.js';

// Endi .at() metodi mavjud
const arr = [1, 2, 3];
console.log(arr.at(-1)); // 3
```

## 14. Dynamic Import (Basic)

**Modulni dastur ishlash vaqtida dinamik ravishda yuklash. Bu kod bo'laklarga ajratish (code splitting) va lazy loading uchun ishlatiladi.**

```js
javascript// heavyLibrary.js
export function processData(data) {
  // Katta hisoblashlar...
  return data.map(x => x * 2);
}

// app.js
// Tugma bosilganda modulni yuklash
document.getElementById('loadBtn').addEventListener('click', async () => {
  // Dynamic import promise qaytaradi
  const module = await import('./heavyLibrary.js');
  
  const result = module.processData([1, 2, 3]);
  console.log(result); // [2, 4, 6]
});
```

## 15. Dynamic Import with Condition

**Shartga qarab turli modullarni yuklash. Bu feature flags yoki user preferences uchun foydali.**

```js
javascript// themes/dark.js
export const theme = {
  background: '#000',
  text: '#fff'
};

// themes/light.js
export const theme = {
  background: '#fff',
  text: '#000'
};

// app.js
async function loadTheme(isDark) {
  // Shartga qarab turli modulni yuklash
  const themeName = isDark ? 'dark' : 'light';
  const module = await import(`./themes/${themeName}.js`);
  
  // Temani qo'llash
  document.body.style.background = module.theme.background;
  document.body.style.color = module.theme.text;
}

// Foydalanish
loadTheme(true); // Dark tema yuklaydi
```

## 16. Dynamic Import with Error Handling

**Dynamic import'da xatolarni to'g'ri boshqarish.**

```js
javascript// app.js

async function loadFeature(featureName) {
  try {
    // Modulni yuklashga urinish
    const module = await import(`./features/${featureName}.js`);
    module.initialize();
    console.log(`${featureName} yuklandi`);
  } catch (error) {
    // Modul topilmasa yoki xato bo'lsa
    console.error(`Xato: ${featureName} yuklanmadi`, error);
    
    // Fallback modulini yuklash
    const fallback = await import('./features/default.js');
    fallback.initialize();
  }
}

loadFeature('premium'); // Agar yo'q bo'lsa, default yuklanadi
```

## 17. Import Map (Basic)

**HTML'da modul yo'llarini qisqartirish va boshqarish uchun import xarita ishlatish.**

```html
html<!DOCTYPE html>
<html>
<head>
  <!-- Import map'ni e'lon qilish -->
  <script type="importmap">
  {
    "imports": {
      "lodash": "https://cdn.skypack.dev/lodash",
      "utils": "./js/utils.js",
      "components/": "./js/components/"
    }
  }
  </script>
</head>
<body>
  <script type="module">
    // Endi qisqa nomlar bilan import qilish mumkin
    import _ from 'lodash';
    import { format } from 'utils';
    import { Button } from 'components/Button.js';
    
    console.log(_.capitalize('hello')); // Hello
  </script>
</body>
</html>
```

## 18. Import Map (Scopes)

**Turli yo'llar uchun turli modul versiyalarini boshqarish.**

```html
html<script type="importmap">
{
  "imports": {
    "react": "https://cdn.skypack.dev/react@18"
  },
  "scopes": {
    "/legacy/": {
      "react": "https://cdn.skypack.dev/react@16"
    },
    "/experimental/": {
      "react": "https://cdn.skypack.dev/react@19"
    }
  }
}
</script>

<script type="module">
  // Fayl joylashuviga qarab turli versiya yuklanadi
  import React from 'react';
  
  // Agar bu fayl /legacy/ papkasida bo'lsa, React 16 yuklanadi
  // Agar /experimental/ da bo'lsa, React 19 yuklanadi
  // Boshqa joylarda React 18 yuklanadi
</script>
```

## 19. Import Map Feature Detection

**Brauzer import map'ni qo'llab-quvvatlaydimi tekshirish.**

```js
javascript// Import map qo'llab-quvvatlanishini tekshirish
if (HTMLScriptElement.supports && HTMLScriptElement.supports('importmap')) {
  console.log('Import map qo\'llab-quvvatlanadi');
  
  // Import map bilan ishlash
} else {
  console.warn('Import map qo\'llab-quvvatlanmaydi');
  
  // Fallback: To'liq URL'lar bilan ishlash
  const script = document.createElement('script');
  script.type = 'module';
  script.src = './full-path-fallback.js';
  document.head.appendChild(script);
}
```

## 20. JSON Import

**JSON fayllarni modul sifatida import qilish. Import attributes bilan resurs turini ko'rsatish majburiy.**

```js
javascript// config.json
{
  "apiUrl": "https://api.example.com",
  "timeout": 5000,
  "features": {
    "darkMode": true,
    "notifications": false
  }
}

// app.js
// JSON'ni import qilish (with attributes kerak!)
import config from './config.json' with { type: 'json' };

console.log(config.apiUrl); // https://api.example.com
console.log(config.timeout); // 5000

// Obyekt sifatida ishlash mumkin
if (config.features.darkMode) {
  enableDarkMode();
}
```

## 21. CSS Import

**CSS fayllarni JavaScript modulida import qilish va Constructable Stylesheets sifatida ishlatish.**

```css
css/* styles.css */
.button {
  background: blue;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 4px;
}
```
```js
javascript// app.js
// CSS'ni import qilish
import styles from './styles.css' with { type: 'css' };

// Hujjatga qo'llash
document.adoptedStyleSheets = [styles];

// Shadow DOM'da ham ishlaydi
class MyButton extends HTMLElement {
  constructor() {
    super();
    const shadow = this.attachShadow({ mode: 'open' });
    
    // Shadow DOM uchun CSS qo'llash
    shadow.adoptedStyleSheets = [styles];
    
    shadow.innerHTML = '<button class="button">Click me</button>';
  }
}
```

## 22. Top Level Await

**Modul darajasida to'g'ridan-to'g'ri await ishlatish. Bu asinxron ma'lumotlarni yuklash va initsializatsiya qilish uchun juda qulay.**

```js
javascript// database.js
// Top level await - async function kerak emas
const response = await fetch('https://api.example.com/config');
const config = await response.json();

// Ma'lumotlarni sozlash
const db = initializeDatabase(config);

// Tayyor ma'lumotlarni eksport qilish
export { db, config };

// users.js
// db tayyor bo'lgunicha kutiladi
import { db } from './database.js';

// db to'liq initsializatsiya bo'lgandan keyin ishlaydi
export async function getUsers() {
  return await db.query('SELECT * FROM users');
}
```

## 23. Module in HTML (External)

**Tashqi JavaScript modul faylini HTML'ga ulash.**

```html
html<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <title>Modul misoli</title>
</head>
<body>
  <div id="app"></div>
  
  <!-- Modul skriptni ulash -->
  <!-- type="module" majburiy! -->
  <script type="module" src="./app.js"></script>
  
  <!-- Modul sifatida defer avtomatik, kerak emas -->
  <!-- Modul strict mode'da avtomatik ishlaydi -->
</body>
</html>
```

## 24. Module in HTML (Inline)

**HTML ichida to'g'ridan-to'g'ri modul kodi yozish.**

```html
html<!DOCTYPE html>
<html>
<head>
  <title>Inline Modul</title>
</head>
<body>
  <button id="loadBtn">Ma'lumot yuklash</button>
  <div id="output"></div>

  <!-- Inline modul kodi -->
  <script type="module">
    // Import ishlaydi
    import { format } from './utils.js';
    
    // Kod
    document.getElementById('loadBtn').addEventListener('click', async () => {
      const response = await fetch('https://api.example.com/data');
      const data = await response.json();
      
      // Ma'lumotni formatlash
      document.getElementById('output').textContent = format(data);
    });
    
    // Modul o'zgaruvchilari global emas
    const privateVar = 'Bu faqat modul ichida ko'rinadi';
  </script>
</body>
</html>
```

## 25. Module Preload

**Kritik modullarni oldindan yuklash orqali performance'ni yaxshilash.**

```html
html<!DOCTYPE html>
<html>
<head>
  <!-- Kritik modullarni oldindan yuklash -->
  <link rel="modulepreload" href="./app.js">
  <link rel="modulepreload" href="./utils.js">
  <link rel="modulepreload" href="./components/Header.js">
  
  <!-- As atributi bilan -->
  <link rel="modulepreload" href="./heavy-library.js" as="script">
</head>
<body>
  <!-- Modul yuklanganidan keyin darhol ishlaydi -->
  <script type="module" src="./app.js"></script>
  
  <!-- Preload qilingan modullar keshdan olinadi -->
  <!-- Bu sahifa yuklash vaqtini sezilarli kamaytiradi -->
</body>
</html>
```

## 26. Nomodule Fallback

**Eski brauzerlar uchun fallback kod. Module'ni qo'llab-quvvatlamaydigan brauzerlar uchun alternativ skript.**

```html
html<!DOCTYPE html>
<html>
<head>
  <title>Fallback misoli</title>
</head>
<body>
  <!-- Zamonaviy brauzerlar uchun modul -->
  <script type="module" src="./modern-app.js"></script>
  
  <!-- Eski brauzerlar uchun bundled kod -->
  <!-- nomodule - faqat modul qo'llab-quvvatlamaydigan brauzerlarda ishlaydi -->
  <script nomodule src="./legacy-bundle.js"></script>
  
  <!-- Bu yondashuv progressive enhancement beradi -->
  <!-- Zamonaviy brauzerlar - zamonaviy kod -->
  <!-- Eski brauzerlar - transpiled va bundled kod -->
</body>
</html>
```

## 27. Live Bindings

**Import qilingan qiymatlar "jonli" - eksport qilingan modul qiymatni o'zgartirsa, import qilingan joy ham o'zgaradi.**

```js
javascript// counter.js
export let count = 0;

export function increment() {
  count++;
}

export function getCount() {
  return count;
}

// app.js
import { count, increment, getCount } from './counter.js';

console.log(count); // 0

increment();
console.log(count); // 1 - qiymat o'zgardi!

increment();
increment();
console.log(getCount()); // 3

// Lekin import qilingan o'zgaruvchini o'zgartirib bo'lmaydi
// count = 10; // Error! Import qilingan qiymat read-only
```

## 28. Cyclic Dependencies (Working)

**Siklik bog'liqliklar asinxron ishlatilganda to'g'ri ishlaydi.**

```js
javascript// a.js
import { b } from './b.js';

// Asinxron ishlatish - ishlaydi
setTimeout(() => {
  console.log('a.js ichida b:', b); // 'B qiymati'
}, 100);

export const a = 'A qiymati';

// b.js
import { a } from './a.js';

// Asinxron ishlatish - ishlaydi
setTimeout(() => {
  console.log('b.js ichida a:', a); // 'A qiymati'
}, 100);

export const b = 'B qiymati';

// main.js
import './a.js';
import './b.js';

// Har ikki modul ham to'g'ri ishlaydi
// Chunki qiymatlar sinxron ishlatilmaydi
```

## 29. Cyclic Dependencies (Broken)

**Siklik bog'liqliklar sinxron ishlatilganda xatoga olib keladi.**

```js
javascript// moduleA.js
import { valueB } from './moduleB.js';

// Sinxron ishlatish - XATO!
console.log('moduleA da valueB:', valueB); // ReferenceError!

export const valueA = 'A dan';

// moduleB.js
import { valueA } from './moduleA.js';

// Sinxron ishlatish - XATO!
console.log('moduleB da valueA:', valueA); // ReferenceError!

export const valueB = 'B dan';

// Muammo:
// 1. moduleA moduleB'ni import qilmoqchi
// 2. moduleB moduleA'ni import qilmoqchi
// 3. Hech biri to'liq yuklanmagan
// 4. Sinxron ishlatish - initialized bo'lmagan qiymat
```

## 30. Avoiding Cyclic Dependencies

**Siklik bog'liqliklardan qochish usullari va yaxshi arxitektura.**

```js
javascript// YOMON: Siklik bog'liqlik
// userService.js
import { log } from './logger.js';
export function createUser() { log('User created'); }

// logger.js
import { createUser } from './userService.js'; // Sikl!
export function log(msg) { console.log(msg); }

// YAXSHI: Uchinchi modulga ajratish
// logger.js - mustaqil
export function log(msg) {
  console.log(`[${new Date().toISOString()}] ${msg}`);
}

// userService.js
import { log } from './logger.js';

export function createUser(name) {
  log('User created');
  return { name, createdAt: Date.now() };
}

// app.js
import { createUser } from './userService.js';
import { log } from './logger.js';

const user = createUser('Ali');
log('Application started');

// Sikl yo'q, hamma narsa toza ishlaydi
```

## 31. Import Hoisting

**Import deklaratsiyalari avtomatik ravishda kodning boshiga "ko'tariladi", lekin yaxshi amaliyot - ularni boshida yozish.**

```js
javascript// app.js

// Bu ishlaydi, chunki import hoisted
console.log(add(2, 3)); // 5

// O'zgaruvchi ishlatiladi
const result = multiply(4, 5);
console.log(result); // 20

// Import deklaratsiyasi kodni istalgan joyida bo'lishi mumkin
import { add } from './math.js';

// Yana kod
const x = add(10, 20);

// Import yana
import { multiply } from './math.js';

// LEKIN yaxshi amaliyot: barcha importlarni boshida yozish
// Bu kodni o'qish va maintain qilish osonlashtiradi
```

## 32. Module Scope

**Modul o'zgaruvchilari global scope'da emas, faqat modul ichida mavjud. Lekin global o'zgaruvchilarga kirish mumkin.**

```js
javascript// module.js
// Bu o'zgaruvchilar faqat modul ichida
const privateVar = 'Bu private';
let moduleData = { count: 0 };

function privateFunction() {
  return 'Bu ham private';
}

// Faqat eksport qilinganlar tashqarida ko'rinadi
export function publicFunction() {
  privateFunction(); // Ichida ishlatish mumkin
  return moduleData.count++;
}

// app.js
import { publicFunction } from './module.js';

publicFunction(); // Ishlaydi
// privateVar // Error! Ko'rinmaydi
// privateFunction() // Error! Ko'rinmaydi
html<!-- HTML'da -->
<script>
  // Global o'zgaruvchi
  var globalData = 'Bu global';
</script>

<script type="module">
  // Modul ichida global'ga kirish mumkin
  console.log(globalData); // 'Bu global'
  console.log(window.globalData); // 'Bu global'
  
  // Lekin modul o'zgaruvchilari tashqarida ko'rinmaydi
  const moduleVar = 'Modul ichida';
</script>

<script>
  // console.log(moduleVar); // Error! Ko'rinmaydi
</script>
```


## 33. Strict Mode Auto-enabled

**Modullar avtomatik ravishda strict mode'da ishlaydi. Alohida 'use strict' yozish kerak emas.**

```js
javascript// module.js
// 'use strict' yozish shart emas - avtomatik

// Strict mode xususiyatlari:
// 1. E'lon qilinmagan o'zgaruvchilar xato
undeclaredVar = 10; // Error!

// 2. O'chirib bo'lmaydigan propertyni o'chirish xato
const obj = {};
Object.defineProperty(obj, 'prop', { 
  value: 10, 
  writable: false 
});
delete obj.prop; // Error!

// 3. with statement ishlatib bo'lmaydi
// with (obj) { } // SyntaxError!

// 4. Oktal literals ishlatib bo'lmaydi
// const num = 0123; // SyntaxError!

// 5. Funksiya parametrlari takrorlanishi mumkin emas
// function test(a, a) { } // SyntaxError!

export function strictFunction() {
  // Bu ham strict mode'da
  arguments.callee; // Error!
}
```

## 34. Multiple Exports from Different Modules

**Bir faylda bir nechta modullardan elementlarni import qilish va ularni boshqarish.**

```js
javascript// services/users.js
export function getUser(id) { return { id, name: 'User' }; }
export function deleteUser(id) { console.log('Deleted', id); }

// services/posts.js
export function getPost(id) { return { id, title: 'Post' }; }
export function deletePost(id) { console.log('Deleted', id); }

// services/comments.js
export function getComment(id) { return { id, text: 'Comment' }; }

// app.js
// Har xil modullardan import
import { getUser, deleteUser } from './services/users.js';
import { getPost, deletePost } from './services/posts.js';
import { getComment } from './services/comments.js';

// Nom to'qnashuvi yo'q, chunki turli modullar
const user = getUser(1);
const post = getPost(1);
const comment = getComment(1);

deleteUser(1);
deletePost(1);
```

## 35. Barrel Exports Pattern

**Bir papkadagi barcha modullarni bitta index.js fayli orqali eksport qilish pattern'i.**

```js
javascript// components/Button.js
export function Button(props) { return '<button>...</button>'; }

// components/Input.js
export function Input(props) { return '<input>...'; }

// components/Select.js
export function Select(props) { return '<select>...'; }

// components/Form.js
export function Form(props) { return '<form>...'; }

// components/index.js (Barrel file)
// Barcha komponentlarni bir joydan eksport qilish
export { Button } from './Button.js';
export { Input } from './Input.js';
export { Select } from './Select.js';
export { Form } from './Form.js';

// Yoki qisqaroq:
export * from './Button.js';
export * from './Input.js';
export * from './Select.js';
export * from './Form.js';

// app.js
// Endi barcha komponentlarni bitta importda olish mumkin
import { Button, Input, Select, Form } from './components/index.js';
// Yoki faqat './components' - agar index.js bo'lsa

const loginForm = Form({
  children: [
    Input({ type: 'text' }),


```
