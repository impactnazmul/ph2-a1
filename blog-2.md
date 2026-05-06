# Using `Pick` and `Omit` to Keep TypeScript Code DRY

## Introduction

In TypeScript, interfaces are often used to describe the structure of objects. However, in real projects, we may not always need the full object shape. Sometimes we need only a few properties, or we need a version without some properties. Instead of creating many repeated interfaces, TypeScript provides utility types such as `Pick` and `Omit`.

## The Problem of Repetition

Suppose we have a master interface for a user:

```ts
interface User {
  id: number
  name: string
  email: string
  password: string
  role: string
}
```

Now imagine we need a public user profile that only shows `id`, `name`, and `email`. One way is to create another interface manually:

```ts
interface PublicUser {
  id: number
  name: string
  email: string
}
```

This works, but it creates duplication. If the type of `email` changes in the main `User` interface, we may also need to update `PublicUser`. This can become difficult to maintain.

## Using `Pick`

The `Pick` utility type allows us to create a new type by selecting specific properties from another type.

```ts
type PublicUser = Pick<User, 'id' | 'name' | 'email'>
```

This means `PublicUser` will include only `id`, `name`, and `email` from the `User` interface. We do not need to rewrite the property types manually.

Example:

```ts
const userProfile: PublicUser = {
  id: 1,
  name: 'John Doe',
  email: 'john@example.com'
}
```

## Using `Omit`

The `Omit` utility type does the opposite. It creates a new type by removing selected properties.

For example, we may want a user object without the password:

```ts
type SafeUser = Omit<User, 'password'>
```

Now `SafeUser` contains all properties from `User` except `password`.

```ts
const safeUser: SafeUser = {
  id: 1,
  name: 'John Doe',
  email: 'john@example.com',
  role: 'admin'
}
```

## How This Keeps Code DRY

DRY means “Don’t Repeat Yourself.” `Pick` and `Omit` help us follow this principle because we can reuse a master interface instead of writing similar interfaces again and again. This reduces mistakes and makes future changes easier.

## Conclusion

`Pick` and `Omit` are useful utility types for creating specialized versions of existing interfaces. `Pick` is helpful when we need only selected properties, while `Omit` is helpful when we need to exclude some properties. Both improve code maintainability and keep TypeScript code cleaner.
