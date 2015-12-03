# Introduction

TypeScript�ĺ���ԭ��֮һ�������ͼ��Ἧ�й�ע���ݵġ��ṹ����shape������һ��Ϊ��ʱ��������Ѽ�����͡���duck typing���򡰽ṹ�����ͻ�����structural subtyping������TypeScript�У��ӿ�����Ϊ��Щ�����������������ã�ͬʱ�ӿ�Ҳ�Ƕ��������֮��Ĺ�ϵ������Ĵ����������Ŀ����֮���ϵ����Ч������

# ���ǵĵ�һ���ӿ�

��������������������򵥵����ӣ����˽�ӿ�����ι����ģ�

```ts
function printLabel(labelledObj: {label: string}) {
    console.log(labelledObj.label);
}

var myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
```

���ͼ��������'printLabel'�ĵ��á�����'printLabel'������һ��������������Ҫ�������������һ��������Ϊ'label'���ַ����������ԵĶ���ע�����Ǵ�����������ʵ���ϲ�ֻ��'label'���ԣ���������ֻ�����Щָ�������ԣ��鿴���ǵ������Ƿ������

��������д��������ӣ�������ǽ�ʹ�ýӿ����������������󣬼�����Ķ���Ҫ���ַ������͵�label���ԡ�

```ts
interface LabelledValue {
    label: string;
}

function printLabel(labelledObj: LabelledValue) {
    console.log(labelledObj.label);
}

var myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
```

���ǿ����������Ϊ'LabelledValue'�Ľӿ�����������ǰ�������е��������Ծɱ�ʾ��Ҫ��һ����Ϊ'label'���ַ������ԡ�ֵ��ע����ǣ�������������Բ�ͬ�����ǲ���Ҫ��ȷ��˵ ����'printLabel'�Ķ���ʵ��������ӿ�(��Ѽ������)������ֻ��ע���ݵġ��ṹ����ֻҪ���Ǵ��������Ķ�������ָ�������������������ǺϷ��ġ�

����ָ�����ǣ����ͼ��������Ҫ����Щ������ѭһ����˳��ֻҪ�ӿ�Ҫ������Դ��ڣ����������ͼ��ɡ�

# ��ѡ����

�ӿ��е����Բ������Ǳ�Ҫ�ġ�����ѭһ��������ʱ����Щ�����������Բ����ڡ��ڴ�����option bags��������ģʽʱ���û�����������Ϊ�����Ķ�������ֻ�����������������档����������£���ѡ���Ծ��Եú������ˡ�

����������ģʽ��һ�����ӣ�

```ts
interface SquareConfig {
    color?: string;
    width?: number;
}

function createSquare(config: SquareConfig): {color: string; area: number} {
    var newSquare = {color: "white", area: 100};
    if (config.color) {
        newSquare.color = config.color;
    }
    if (config.width) {
        newSquare.area = config.width * config.width;
    }
    return newSquare;
}

var mySquare = createSquare({color: "black"});
```

������������ѡ����ʱ��Ҫ����'?'��Ϊ��ʶ���⣬���п�ѡ���ԵĽӿڵ�д���������ӿ����ơ�

ʹ�ÿ�ѡ���Ե��������ڣ����ǿ������������ܴ��ڵ����Ե�ͬʱ����׽��Щ���ǲ�ϣ�����ڵ����ԡ�������˵��������Ǵ����ƴд�˴���'createSquare'�������������Ļ����ͻ���һ��������Ϣ��ʾ���ǣ�

```ts
interface SquareConfig {
    color?: string;
    width?: number;
}

function createSquare(config: SquareConfig): {color: string; area: number} {
    var newSquare = {color: "white", area: 100};
    if (config.color) {
        // �������� 'SquareConfig' û����Ϊ 'collor' ������
        newSquare.color = config.collor;
    }
    if (config.width) {
        newSquare.area = config.width * config.width;
    }
    return newSquare;
}

var mySquare = createSquare({color: "black"});
```

# ��������

�ӿڿ���������ʽ������JavaScript����Ȼ�����ǳ����ýӿ�������һ��������������⣬Ҳ���������������������͡�

������Ҫ���ӿ�һ�����ñ���������������͡���������������ֻ�в����б�ͷ������͵ĺ����Ķ��塣�����Ϳ���ö�ٺ��������в��������ƺ����͡�

```ts
interface SearchFunc {
    (source: string, subString: string): boolean;
}
```

�����������ӿ��Ժ����ǾͿ�����ʹ�������ӿ�һ��ʹ������������ͽӿڡ�����չʾ������Ҫ��δ���һ���������ͱ�����������ֵһ��ͬ�����͵ĺ���ֵ��

```ts
var mySearch: SearchFunc;
mySearch = function(source: string, subString: string) {
    var result = source.search(subString);
    if (result == -1) {
        return false;
    }
    else {
        return true;
    }
}
```

���ں������ͽӿڵ����ͼ�飬�����������������ӿ��еĲ������Ʋ�һ�¡�����˵���������Ҳ������ôд��

```ts
var mySearch: SearchFunc;
mySearch = function(src: string, sub: string): boolean {
    var result = src.search(sub);
    if (result == -1) {
        return false;
    }
    else {
        return true;
    }
}
```

�ڶԺ����Ĳ����������ͼ��ʱ��ֻ�����ڽӿڶ�Ӧλ���ϵĲ��������������Ƿ�һ�£��������޹ء�
������ں�������ʱû��ָ�����ͣ����������src��sub������ôTypeScript������㵱ǰ�������������Ϣ�Ƶ����˺�������SearchFunc�ӿڣ��Ӷ��Զ���Ϊsrc��sub��������string��
������Ҳ��Ժ������ʽ�ķ������ͽ��м�飨������true��false����
������ﺯ�����ص������ֻ��ַ����������ͼ�����ͻᾯ�����Ƿ��ص�������SearchFunc�ӿڲ������

```ts
var mySearch: SearchFunc;
mySearch = function(src, sub) {
    // �����src��sub��string��������any
    var result = src.search(sub);
    if (result == -1) {
        return false;
    }
    else {
        return true;
    }
}
```

# ��������

����Ҳ�����ýӿ��������������ͣ�����������ʽ�뺯���������ơ��������ͻ���һ��'index'���ͣ�������������ʾ���������������±꣩�����͡�ͬ������Ҳ��Ҫ��������Ӧ�ķ���ֵ�����͡�

```ts
interface StringArray {
    [index: number]: string;
}

var myArray: StringArray;
myArray = ["Bob", "Fred"];
```

TypeScript֧�������������ͣ�string��number��ͬʱʹ�����������͵�����Ҳ������ģ�ֻҪ���Ǳ�֤number���͵���������Ӧ�ķ���������string������Ӧ�ķ������͵������͡�

��Ȼ������ʶ������������ֵ����͵����ݵĺ÷�������ͬʱҲ��ǿ�������������Զ��������ķ���������ͬ��
������Ϊ`obj.property`Ҳ����һ��`obj["property"]`�������ַ���������
������������У�'name'���Ե����Ͳ����������ķ������ͣ���ᵼ�����ͼ���׳�����

```ts
interface NumberDictionary {
    [index: string]: number;
    length: number;    // ��ȷ��length��number����
    name: string;      // ����name�ķ�������string����number�������͡�
}
```

# ��

## ʵ�ֽӿ�

��C#��Java�У���һ�������ĳ���ض���Լ������һ�ֺܳ����Ľӿڵ�ʹ�÷�ʽ����TypeScript������Ҳ��������ʹ�ýӿڡ�

```ts
interface ClockInterface {
    currentTime: Date;
}

class Clock implements ClockInterface {
    currentTime: Date;
    constructor(h: number, m: number) { }
}
```

���ǿ�����һ���ӿ�������һ������Ҫʵ�ֵķ�������������������е�`setTime`������

```ts
interface ClockInterface {
    currentTime: Date;
    setTime(d: Date);
}

class Clock implements ClockInterface {
    currentTime: Date;
    setTime(d: Date) {
        this.currentTime = d;
    }
    constructor(h: number, m: number) { }
}
```

�ӿ�ֻ��������Ĺ������֣�������ע˽�в��֡����ֻ��Ʋ���������ͨ���ӿ������һ�����ʵ����˽�в��֡�

## ��ľ�̬��ʵ���Ĳ���

��ʹ����ͽӿ�ʱ������Ӧ��Ҫ�ǵ�һ�����о�̬���ֺ�ʵ�����еĲ��֡������ע�⵽�ˣ��������һ�����й��캯����ǵĽӿڣ������Դ���һ������ʵ������ӿڵĻ������ǻ��յ�����

```ts
interface ClockConstructor {
    new (hour: number, minute: number);
}

class Clock implements ClockConstructor {
    currentTime: Date;
    constructor(h: number, m: number) { }
}
```

������Ϊ��һ����ʵ��һ���ӿ�ʱ��ֻ��ʵ���Ĳ��ֻᱻ���м�顣���캯�����ھ�̬�Ĳ��֣��������ڼ��ķ�Χ֮�ڡ�

��Ӧ�أ�����Ӧ��ֱ�Ӽ����ľ�̬���֡�
����������У����������������ӿڣ�`ClockConstructor` �ӿ����ڹ��죬`ClockInterface`�ӿ�����ʵ���ķ�����
Ȼ������Ϊ������ã�������һ��`createClock`�������ڴ���ʵ�������������ݸ�ʵ����

```ts
interface ClockConstructor {
    new (hour: number, minute: number): ClockInterface;
}
interface ClockInterface {
    tick();
}

function createClock(ctor: ClockConstructor, hour: number, minute: number): ClockInterface {
    return new ctor(hour, minute);
}

class DigitalClock implements ClockInterface {
    constructor(h: number, m: number) { }
    tick() {
        console.log("beep beep");
    }
}
class AnalogClock implements ClockInterface {
    constructor(h: number, m: number) { }
    tick() {
        console.log("tick tock");
    }
}

var digital = createClock(DigitalClock, 12, 17);
var analog = createClock(AnalogClock, 7, 32);
```

Because `createClock`'s first parameter is of type `ClockConstructor`, in `createClock(AnalogClock, 12, 17)`, it checks that `AnalogClock` has the correct constructor signature.
��Ϊ`createClock`�ĵ�һ�������ǽӿ�����`ClockConstructor`���ڷ���`createClock(AnalogClock, 12, 17)`�ĵ����У������`AnalogClock`�Ĺ�������Ƿ���Ͻӿ�ǩ����

# ��չ�ӿ�

ͬ��һ�����ӿ�Ҳ�����໥��չ����չ���Ƹ���һ���ӿ��еĳ�Ա��������һ���ӿ��У�����ζ�����ǿ��Ը����Լ�����Ը�ѽӿڷ���ɿ����õ������

```ts
interface Shape {
    color: string;
}

interface Square extends Shape {
    sideLength: number;
}

var square = <Square>{};
square.color = "blue";
square.sideLength = 10;
```

���ӿڿ�����չ����ӿڣ��Ӷ���Ϊ����ӿڵ���ϡ�

```ts
interface Shape {
    color: string;
}

interface PenStroke {
    penWidth: number;
}

interface Square extends Shape, PenStroke {
    sideLength: number;
}

var square = <Square>{};
square.color = "blue";
square.sideLength = 10;
square.penWidth = 5.0;
```

# �������

��������֮ǰ�ᵽ���ģ��ӿڿ���������ʵ��JavaScript���ܱ��ֵķḻ���������͡�����JavaScript��̬���������ԣ�������ʱ���ܻ�������Ҫ�ۺ�ʹ��ǰ�������Ľӿڵ�ʹ�÷�����������һ��������龰��

�ٸ����ӣ�һ���������һ��������ͬʱ������һ����������һ����������ԡ�

```ts
interface Counter {
    (start: number): string;
    interval: number;
    reset(): void;
}

function getCounter(): Counter {
    var counter = <Counter>function (start: number) { };
    counter.interval = 123;
    counter.reset = function () { };
    return counter;
}

var c = getCounter();
c(10);
c.reset();
c.interval = 5.0;
```

��ͬ������JavaScript������н���ʱ�����ǿ��ܾ���Ҫʹ�������ģʽ��������������һ�����ݵ����ͺͽṹ��

# �ӿ���չ��

���ӿڼ̳���һ��������ʱ������̳���ĳ�Ա����������ʵ�֡�
�ͺ���ӿ��������������д��ڵĳ�Ա������û���ṩ����ʵ��һ����
�ӿ�ͬ����̳е����private��protected��Ա��
����ζ�ŵ��㴴����һ���ӿڼ̳���һ��ӵ��˽�л��ܱ����ĳ�Ա����ʱ������ӿ�����ֻ�ܱ���������������ʵ�֣�implement����

���Ǻ����õģ�������һ�������εļ̳У�����ֻ����Ĵ���ֻ�����ӵ���ض����Ե����������õ�ʱ��������˼̳��Ի����������û���κ���ϵ��
����

```ts
class Control {
    private state: any;
}

interface SelectableControl extends Control {
    select(): void;
}

class Button extends Control {
    select() { }
}

class TextBox extends Control {
    select() { }
}

class Image extends Control {
}

class Location {
    select() { }
}
```
������������`SelectableControl`������`Control`�����г�Ա������˽�г�Ա`state`��
��Ϊ`state`��˽�г�Ա������ֻ�ܹ���`Control`�������ǲ���ʵ��`SelectableControl`�ӿڡ�
��Ϊֻ��`Control`��������ܹ�ӵ��һ��������`Control`��˽�г�Ա`state`�����˽�г�Ա�ļ������Ǳ���ġ�

��`Control`���ڲ���������ͨ��`SelectableControl`��ʵ��������˽�г�Ա`state`�ġ�
ʵ���ϣ�`SelectableControl`����`Control`һ������ӵ��һ��`select`������
`Button`��`TextBox`����`SelectableControl`�����ࣨ��Ϊ���Ƕ��̳���`Control`����`select`����������`Image`��`Location`�ಢ���������ġ�

# ��л����
- oyyd      https://github.com/oyyd/typescript-handbook-zh
- ��д����  https://github.com/MyErpSoft/TypeScript-Handbook
- zhongsp   https://github.com/zhongsp/TypeScript