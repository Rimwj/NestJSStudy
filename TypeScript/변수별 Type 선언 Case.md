# TypeScript Type Inference vs Type Annotations

## Type Inference
TypeScript can automatically set the type of variables based on the assigned values. Here is how TypeScript infers the type for each variable:

```typescript
{
    let apples = 5; // inferred as number
    let speed = 'fast'; // inferred as string
    let isActive = false; // inferred as boolean
    let nothingMuch = null; // inferred as null
    let nothing = undefined; // inferred as undefined
    let now = new Date(); // inferred as Date
    let color = ['red', 'green', 'blue']; // inferred as string[]
    let numbers = [1, 2, 3]; // inferred as number[]
    let truths = [true, false, true]; // inferred as boolean[]
}
```

## Type Annotations
You can explicitly set the type of variables. This provides TypeScript with exact type information.

```typescript
{
    let apples: number = 5;
    let speed: string = 'fast';
    let isActive: boolean = false;
    let nothingMuch: null = null;
    let nothing: undefined = undefined;
    let now: Date = new Date();
    let color: string[] = ['red', 'green', 'blue'];
    let numbers: number[] = [1, 2, 3];
    let truths: boolean[] = [true, false, true];
}
```

## When Type Inference Is Not Enough

There are cases where TypeScript's type inference is not sufficient. For example, the return type of `JSON.parse` can be quite varied, necessitating explicit type annotations.

```typescript
{
    const json = '{"x":10,"y":20}';
    let coordinates = JSON.parse(json); // `coordinates` is treated as `any` type

    // Since `JSON.parse` can return multiple types, explicit type annotation is necessary for `coordinates`.
    coordinates.thisisnothing = 1;
    coordinates = 123123;

    // Solve it by using explicit type annotations
    interface Point {
        x: number;
        y: number;
    }

    let coordinates2: Point = JSON.parse(json);
}
```
