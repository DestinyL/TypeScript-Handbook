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

Ԫ������������̶���������֪���ͼ��ϣ�����Щ���Ͳ�������ͬ�ġ����磬���������ʾһ��'string`��`number`��ϵ����ͣ�

```ts
// ����һ��Ԫ������
var x: [string, number];
// ��ʼ����
x = ['hello', 10]; // ׼ȷ
// ����ĳ�ʼ��
x = [10, 'hello']; // ����
```

���ǿ���ʹ�����ּ���һ����֪��Ԫ�أ�����Ҫע��������ȷ��

```ts
console.log(x[0].substr(1)); // ��ȷ
console.log(x[1].substr(1)); // ����'number' ����û�� 'substr' ����
```

�����ʵ����������߽�ʱ����ʹ���������ʹ���

```ts
x[3] = 'world'; // ��ȷ��string�������䵽 (string | number)
console.log(x[5].toString()); // ��ȷ��'string' �� 'number' ���� toString ����
x[6] = true; // ���󣬲���ֵ���� (string | number) �е�һ��
```

���������Ǹ��߼������⣬���ǻ��ں������½��н��ܡ�

# Enum ö��

TypeScript��չ��JavaScriptԭ���ı�׼�������ͼ���������ö�����ͣ�enum����ö����һ�ֺ����õ��������ͣ�����C#��������һ�������ṩ��һ�ָ��������͵�ֵ���������ڱ������ֵķ�����

```ts
enum Color {Red, Green, Blue};
var c: Color = Color.Green;
```

��Ĭ������£�ö�����ͻ������0��ʼ�������Ԫ�ء����ǿ���ͨ����Ϊ������Ԫ�ص���ֵ���ı�Ĭ��ֵ�����磬������������ǿ������óɴ�1��ʼ������

```ts
enum Color {Red = 1, Green, Blue};
var c: Color = Color.Green;
```

�����������Ը����е�ö��Ԫ��������ֵ��

```ts
enum Color {Red = 1, Green = 2, Blue = 4};
var c: Color = Color.Green;
```

ö��������һ��������ԣ�����Ҳ����ֱ������ֵ���������Ӧ��ö��Ԫ�ص����ơ�������˵�����������һ��ֵΪ2,�����ǲ�ȷ�������ֵ��Ӧö�������е��ĸ�Ԫ�أ������ǿ���ֱ�Ӳ��������ֵ��Ӧ�����ƣ�

```ts
enum Color {Red = 1, Green, Blue};
var colorName: string = Color[2];

alert(colorName);
```

# Any 

�����Ǳ�дӦ��ʱ�����ǿ��ܻ���Ҫ����һЩ���Ͳ���ȷ�ı�������Ϊ��Щ������ֵ������Դ��һЩ��̬�����ݣ����û���������ṩ�Ŀ⡣����������£�������Ҫ�Թ�����Щ�������е����ͼ�飬������ֱ��ͨ������ʱ�ļ�顣Ϊ��ʵ����һĿ�ģ����ǿ��԰����Ǳ�ʶΪ'any'���ͣ�

```ts
var notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean
```

ʹ��'any'�����Ǵ����������е�JavaScript�����һ��ǿ��ķ�ʽ�����ǿ��������������ӻ�����ڱ�������е����ͼ�顣
������������������������������ʹ��`Object`��ʵ��������ܣ�����ע����JavaScript�У�`Object`���ͽ��������������ֵ�����������ܵ������Ĵ��ڻ���ܵ��κη�����

```ts
var notSure: any = 4;
notSure.ifItExists(); // û���⣬������ʱ�п����� ifItExists �������
notSure.toFixed(); // û���⣬toFixed ����ʵ���ڵķ��� (���Ǳ�����������֤׼ȷ��)
var prettySure: Object = 4;
prettySure.toFixed(); // ���󣬲��о��ǲ����ˣ�ʹ��any��
```

������֪��һ�����͵Ĳ����������ͣ�ȴ�ֲ�ȷ�����е���������ʱ��ʹ��'any'����Ϊ�����ṩ���ٷ��㡣��������һ�����飬������������е�Ԫ�����ڲ�ͬ���������ͣ����������ô����

```ts
var list: any[] = [1, true, "free"];

list[1] = 100;
```

# Void

`void`����`any`���෴�棺void����û�У�any�������С�û�з���ֵ�ĺ����Ϳ�����Ϊ��'void'���ͣ�

```ts
function warnUser(): void {
    alert("This is my warning message");
}
```

����������һ�������� `void`���ͣ���Ϊ���������ֻ�ܸ�ֵ`undefined` �� `null`��

```ts
var unusable: void = undefined;
```

# ��л����
- oyyd      https://github.com/oyyd/typescript-handbook-zh
- ntesmail  https://github.com/ntesmail/Typescript-Handbook
- ��д����  https://github.com/MyErpSoft/TypeScript-Handbook


