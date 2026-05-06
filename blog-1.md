# Why `any` Is a Type Safety Hole and `unknown` Is Safer

## Introduction

TypeScript is useful because it helps developers catch mistakes before running the code. However, using the `any` type can remove many of TypeScript’s benefits. Although `any` may feel convenient, it creates a type safety hole because TypeScript stops checking the value properly. A safer alternative is `unknown`, especially when working with unpredictable data.

## Why `any` Is Risky

The `any` type tells TypeScript to allow anything. Once a value is typed as `any`, TypeScript will not warn us even if we perform unsafe operations.

```ts
let data: any = 'Hello'

console.log(data.toUpperCase())
console.log(data.toFixed(2))
```

The first operation works because `data` is a string. However, `toFixed()` is a number method, so this will cause a runtime error. TypeScript does not stop it because `data` is typed as `any`.

This is why `any` is called a type safety hole. It bypasses the checking system and makes TypeScript behave more like plain JavaScript.

## Why `unknown` Is Safer

The `unknown` type also allows a value to be unpredictable, but it does not allow unsafe use without checking the type first.

```ts
let data: unknown = 'Hello'

console.log(data.toUpperCase())
```

This code will show an error because TypeScript does not yet know whether `data` is really a string. Before using it, we must narrow the type.

```ts
let data: unknown = 'Hello'

if (typeof data === 'string') {
  console.log(data.toUpperCase())
}
```

Now TypeScript allows the operation because the `typeof` check confirms that `data` is a string.

## Type Narrowing

Type narrowing means checking a broad type and reducing it to a more specific type. TypeScript can then safely understand what operations are allowed.

Example:

```ts
function printValue(value: unknown): string {
  if (typeof value === 'string') {
    return value.toUpperCase()
  }

  if (typeof value === 'number') {
    return value.toFixed(2)
  }

  return 'Unsupported value'
}
```

Here, the function safely handles different types using type guards.

## Conclusion

The `any` type should be avoided when possible because it removes TypeScript’s protection. The `unknown` type is safer because it forces developers to check the value before using it. This makes the code more reliable, easier to debug, and better aligned with TypeScript’s purpose.
