# B7A1 - Advanced Problem Solving with TypeScript & OOP

This repository contains my submission for the B7A1 assignment. The assignment includes TypeScript problem-solving tasks and two technical blog posts written in Markdown.

## Repository Structure

```text
├── solutions.ts
├── blog-1.md
├── blog-2.md
├── README.md
├── package.json
└── tsconfig.json
```

## Technologies Used

- TypeScript
- Node.js

## TypeScript Solutions

All coding solutions are placed in `solutions.ts`.

### Problem 1: Filter Even Numbers

The `filterEvenNumbers` function takes an array of numbers and returns a new array containing only the even numbers.

```ts
function filterEvenNumbers(numbers: number[]): number[] {
  return numbers.filter((num: number): boolean => num % 2 === 0)
}
```

It uses the `filter()` method to check each number. If a number is divisible by `2` with no remainder, it is even.

---

### Problem 2: Reverse a String

The `reverseString` function takes a string and returns the reversed version of it.

```ts
function reverseString(input: string): string {
  return input.split('').reverse().join('')
}
```

The string is first converted into an array using `split('')`, then reversed using `reverse()`, and finally joined back into a string using `join('')`.

---

### Problem 3: Union Type and Type Guard

The `StringOrNumber` type allows a value to be either a string or a number.

```ts
type StringOrNumber = string | number
```

The `checkType` function uses the `typeof` operator as a type guard.

```ts
function checkType(value: StringOrNumber): string {
  if (typeof value === 'string') {
    return 'String'
  }

  return 'Number'
}
```

If the value is a string, the function returns `"String"`. Otherwise, it returns `"Number"`.

---

### Problem 4: Generic Function with Key Constraint

The `getProperty` function takes an object and a key, then returns the value of that key.

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key]
}
```

Here, `T` represents the object type. `K extends keyof T` means the key must exist inside the object. The return type `T[K]` means the function returns the exact type of the selected property.

This prevents invalid keys from being used.

---

### Problem 5: Interface and Extended Object

The `Book` interface defines the structure of a book object.

```ts
interface Book {
  title: string
  author: string
  publishedYear: number
}
```

The `BookWithReadStatus` interface extends `Book` by adding an `isRead` property.

```ts
interface BookWithReadStatus extends Book {
  isRead: boolean
}
```

The `toggleReadStatus` function returns a new object with the original book properties and an added `isRead: true` property.

```ts
function toggleReadStatus(book: Book): BookWithReadStatus {
  return {
    ...book,
    isRead: true
  }
}
```

The spread operator is used so that the original book object is not changed directly.

---

### Problem 6: Class and Inheritance

The `Person` class contains common properties: `name` and `age`.

```ts
class Person {
  name: string
  age: number

  constructor(name: string, age: number) {
    this.name = name
    this.age = age
  }
}
```

The `Student` class extends `Person` and adds a new property called `grade`.

```ts
class Student extends Person {
  grade: string

  constructor(name: string, age: number, grade: string) {
    super(name, age)
    this.grade = grade
  }

  getDetails(): string {
    return `Name: ${this.name}, Age: ${this.age}, Grade: ${this.grade}`
  }
}
```

The `super(name, age)` call passes the name and age values to the parent `Person` class. The `getDetails()` method returns the student's information in the required format.

---

### Problem 7: Intersection of Two Arrays

The `getIntersection` function takes two arrays of numbers and returns the numbers that exist in both arrays.

```ts
function getIntersection(
  firstArray: number[],
  secondArray: number[]
): number[] {
  return firstArray.filter((num: number): boolean => secondArray.includes(num))
}
```

It uses `filter()` to go through the first array and `includes()` to check whether each number also exists in the second array.

## Blog Posts

This repository also includes two Markdown blog posts:

- `blog-1.md`
- `blog-2.md`

Each blog post includes a title, introduction, body paragraphs with code examples, and a conclusion.

## How to Check the Code

Install dependencies:

```bash
npm install
```

Compile the TypeScript file:

```bash
npm run compile
```

## Assignment Requirements Followed

- All TypeScript solutions are written in a single file named `solutions.ts`
- Function names follow the assignment instructions
- Return values match the required sample outputs
- No `console.log` statements are included in `solutions.ts`
- Blog posts are written as separate Markdown files
