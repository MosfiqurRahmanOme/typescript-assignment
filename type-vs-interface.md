# Type vs Interface in TypeScript

## Introduction

Type aliases and interfaces are the two ways in TypeScript to define the types and structure of data. A type alias is generally connected to unions, tuples, literals, and primitives, while an interface is mainly used to describe object. 

### Examples

### Type alias

```typescript
type ID = number;
type User = "admin" | "manager";
```
### Interface

```typescript
interface Car {

    model: "axio",
    brand: "toyota"
}
 
```

### 1. Declaration merging

Interfaces with the same name merge automatically. Type aliases cannot be redeclared.

```typescript
// interface: same name twice merges automatically

interface IEmployee {
    name: string;
}

interface IEmployee {
    id: number;
}

const employee: IEmployee = {
    name: "HDEJ",
    id: 23,
}
```

```typescript
//type alias: cannot be redeclared
type TEmployee = {
    name: string;
}

type TEmployee = {    // Duplicate identifier
}
```

### 2. Extending

Interfaces use `extends`, while type aliases use intersection (`&`).

```typescript
// interface uses extends
interface Animal {
    species: string;
}

interface Cat extends Animal {
    breed: string;
}

const cat: Cat = {
    breed: "persian",
    species: "Catus"
}
```

```typescript
// type alias uses intersection (&)
type Vehicle = {
    brand: string;
}

type Car = Vehicle & {  //? "&" is used to perform imtersection
    model: string;
}

const car: Car =  {
    model: "axio",
    brand: "toyota"
}

```

## When to Choose Which

**Choose `interface` when:**

- describing an object shape (`User`, `Course`)
-  extend or merge

**Choose `type` when:**

- union, tuple, literal or primitive

```typescript
// type: things interface cannot express
type Status = "active" | "inactive";
type Coordinate = readonly [number, number];
type ID = string | number;

// interface: object shape
interface Course {
  title: string;
  students: number;
  isPublished: boolean;
}
```

## Conclusion

Both work for plain object shapes, so the choice depends on what you need to express. Use an interface for object structures and class contracts, and use a type alias when you need unions, tuples, or other advanced types. Most importantly, stay consistent across the project.
