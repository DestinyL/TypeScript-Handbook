# Introduction

Ϊ���ó�������ã����Ǽ��ݼ�����������������ͣ�numbers(����)��strings(�ַ���)��structures(�ṹ)��boolean(����ֵ)�ȵȡ��� TypeScript �У�����֧�ֺ� Javascript ����һ��������ͣ�����������ʵ�õ�ö�����͡�

# Boolean ����ֵ

��������������;��Ǽ򵥵� true(��)/false(��) ���� Javascript �� TypeScript ���Լ��������ԣ��б������� "boolean(����ֵ)"��

```ts
var isDone: boolean = false;
```

# Number ����

�� Javascript һ������ TypeScript �����е�number���Ǹ���ֵ��
TypeScript ����֧��ECMAScript 2015�е�ʮ�����ƺ�ʮ�����⣬��֧�ֶ����ƺͶ��������͡�

```ts
var decLiteral: number = 6;
var hexLiteral: number = 0x9837abdef;
var binaryLiteral: number = 0b0010;
var octalLiteral: number = 0o74563;
```

# String �ַ���

��ʹ��JavaScript������ҳ��Ӧ�ó���ʱ��Ҫ�õ��ܻ����Ĺ����Ǵ����ַ���������������һ��������ʹ�� "string" ��������ʾ��Щ�ı����ݡ��� JavaScript һ����TypeScript Ҳʹ��˫���Ż�������Χ���ַ������ݡ�

```ts
var name: string = "bob";
name = 'smith';
```

��Ҳ����ʹ�� *ģ���ַ���*������֧�ֶ����ı�����Ƕ���ʽ����Щ�ַ���ʹ�õ�����(`` ` ``)��Χ������Ƕ��ı��ʽʹ��`${ expr }`��������ʽ��ʾ��

```ts
var name: string = `Gene`;
var age: number = 37;
var sentence: string = `Hello, my name is ${ name }.

I'll be ${ age + 1 } years old next month.`
```

����ı��ʽ�൱�������������ʽ��

```ts
var sentence: string = "Hello, my name is " + name + ".\n\n" +
    "I'll be " + (age + 1) + " years old next month."
```

# Array ����

TypeScript �� Javascript һ����������ʹ�����顣�������͵Ķ������������д������һ��д������������Ԫ�����ͺ�����ӡ�[]������ʾ����һ�������͵�����:

```ts
var list: number[] = [1, 2, 3];
```

�ڶ���д��ʹ��һ��ͨ�õ��������ͱ�ʾ��Array<����Ԫ������>:

```ts
var list: Array<number> = [1, 2, 3];
```

# Tuple Ԫ��

Tuple types allow you to express an array where the type of a fixed number of elements is known, but need not be the same.
For example, you may want to represent a value as a pair of a `string` and a `number`:

```ts
// Declare a tuple type
var x: [string, number];
// Initialize it
x = ['hello', 10]; // OK
// Initialize it incorrectly
x = [10, 'hello']; // Error
```

When accessing an element with a known index, the correct type is retrieved:

```ts
console.log(x[0].substr(1)); // OK
console.log(x[1].substr(1)); // Error, 'number' does not have 'substr'
```

When accessing an element outside the set of known indices, a union type is used instead:

```ts
x[3] = 'world'; // OK, string can be assigned to (string | number)
console.log(x[5].toString()); // OK, 'string' and 'number' both have toString
x[6] = true; // Error, boolean isn't (string | number)
```

Union types are an advanced topic that we'll cover in a later chapter.

# Enum

A helpful addition to the standard set of datatypes from JavaScript is the `enum`.
As in languages like C#, an enum is a way of giving more friendly names to sets of numeric values.

```ts
enum Color {Red, Green, Blue};
var c: Color = Color.Green;
```

By default, enums begin numbering their members starting at `0`.
You can change this by manually setting the value of one its members.
For example, we can start the previous example at `1` instead of `0`:

```ts
enum Color {Red = 1, Green, Blue};
var c: Color = Color.Green;
```

Or, even manually set all the values in the enum:

```ts
enum Color {Red = 1, Green = 2, Blue = 4};
var c: Color = Color.Green;
```

A handy feature of enums is that you can also go from a numeric value to the name of that value in the enum.
For example, if we had the value `2` but weren't sure what that mapped to in the `Color` enum above, we could look up the corresponding name:

```ts
enum Color {Red = 1, Green, Blue};
var colorName: string = Color[2];

alert(colorName);
```

# Any

We may need to describe the type of variables that we do not know when we are writing an application.
These values may come from dynamic content, e.g. from the user or a 3rd party library.
In these cases, we want to opt-out of type-checking and let the values pass through compile-time checks.
To do so, we label these with the `any` type:

```ts
var notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean
```

The `any` type is a powerful way to work with existing JavaScript, allowing you to gradually opt-in and opt-out of type-checking during compilation.
You might expect `Object` to play a similar role, as it does in other languages.
But variables of type `Object` only allow you to assign any value to them -- you can't call arbitrary methods on them, even ones that actually exist:

```ts
var notSure: any = 4;
notSure.ifItExists(); // okay, ifItExists might exist at runtime
notSure.toFixed(); // okay, toFixed exists (but the compiler doesn't check)
var prettySure: Object = 4;
prettySure.toFixed(); // Error: Property 'toFixed' doesn't exist on type 'Object'.
```

The `any` type is also handy if you know some part of the type, but perhaps not all of it.
For example, you may have an array but the array has a mix of different types:

```ts
var list: any[] = [1, true, "free"];

list[1] = 100;
```

# Void

`void` is a little like the opposite of `any`: the absence of having any type at all.
You may commonly see this as the return type of functions that do not return a value:

```ts
function warnUser(): void {
    alert("This is my warning message");
}
```

Declaring variables of type `void` is not useful because you can only assign `undefined` or `null` to them:

```ts
var unusable: void = undefined;
```

# ��л����
��д����  https://github.com/MyErpSoft/TypeScript-Handbook
ntesmail  https://github.com/ntesmail/Typescript-Handbook
oyyd      https://github.com/oyyd/typescript-handbook-zh
