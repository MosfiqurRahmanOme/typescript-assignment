# Combining Union (`|`) and Intersection (`&`) Types in TypeScript

## Introduction

Union (`|`) and Intersection (`&`) are two important features of
TypeScript. Union types allow a variable to have multiple possible
types, while intersection types combine multiple types into one.

## Examples

### 1. Union Type (`|`)

Union allows a value to be one of several types.

``` typescript
type ID = string | number;

let userId: ID = 101;
let UserId1: ID = "USER001";
```

`userId` can be either a string or a number.

### 2. Intersection Type (`&`)

Intersection combines multiple types into one type.

``` typescript
type User = {
    name: string;
    email: string;
}

type Admin = {
    role: string;
}

type AdminUser = User & Admin;

const admin: AdminUser = {
    name: "fahad",
    email: "fahad@gmail.com",
    role: "admin",

}
```

Here, `AdminUser` combines all properties from both `User` and `Admin`.

### 3. Combining Union and Intersection

We can combine both operators to create more practical types.

``` typescript
type BasicUser = {
    name: string;
    age: number;
}

type Admin = {
    role: "admin";
    permissions: string[];
}

type Customer = {
    role: "customer";
    purchaseCount: number;
}

// Intersection combines object properties
type User = BasicUser & (Admin | Customer);

const admin: User = {
    name: "Rahim",
    age: 25,
    role: "admin",
    permissions: ["read", "write"]
}

const customer: User = {
    name: "Karim",
    age: 30,
    role: "customer",
    purchaseCount: 5
}
```

Here: - `Admin | Customer` means the user can  an Admin or a
Customer. - `BasicUser & (...)` means both types must include the basic
user properties. - So, every user must have `name` and `age`, along with
either admin-specific or customer-specific properties.


## Conclusion

Union (`|`) allows us to choose between multiple types, while
Intersection (`&`) combines multiple types together.
