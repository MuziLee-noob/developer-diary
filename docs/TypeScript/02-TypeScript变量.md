# TypeScript基础

## 1.1 数据类型

### 原始类型

1. number

   ```typescript
   let size: number = 18
   let score: number = 99.9
   
   let salary: number = 10000
   let salaryWithGirlFriend: number = -2000
   ```

2. string

   字符串推荐使用单引号

   ```typescript
   let food: string = '糖葫芦'
   ```

3. boolean

   ```typescript
   let isStudying: boolean = true
   let isPlaying: boolean = false
   ```

4. undefined、null

   undefined 类型的值为：undefined，表示声明但未赋值的变量值（找不到值）

   null 类型的值为：null，表示声明了变量但赋值为null

   ```typescript
   let u: undefined = undefined
   let n: null = null
   ```

### 对象类型

#### 数组 object

类型 + []

```typescript
let names: string[] = ['迪丽热巴', '古力娜扎', '马尔扎哈']
```

##### 内置函数

1. forEach

   回调函数的参数为实参，不需要指定类型注解，forEach遍历数组时无法用return阻止

   ```typescript
   let songs: string[] = ['五环之歌', '探清水河', '晴天']
   songs.forEach(function(item, index) => {})
   let nums: number[] = [1, 123, 24, 256]
   nums.forEach(function(num, index) => {})
   ```

2. some

   遍历数组，查找是否有一个满足条件的元素

   **循环特点**：根据返回值决定是否停止循环，true 停止，false 继续，默认为 false

   **返回值**：布尔值，如果找到满足条件的元素，结果为 true，否则为 false

   ```typescript
   // 判断一个数组中是否有大于10的数字
   let nums: number[] = [1, 12, 9, 8, 6]
   let flag = false
   nums.some(function(num, index) {
             if (num > 10) {
       		flag = true
       		return true
   		 }
   })
   
   ```

   

#### 函数 function

```typescript
function getSum(nums: number[], name: string, age: number): void { // 无返回值
    let sum: number = 0
    for (let i: number = 0; i < nums.length; i++) {
        sum += nums[i]
    }
    console.log(sum)
}

function getSum(nums: number[]): number {
    let sum: number = 0
    for (let i: number = 0; i < nums.length; i++) {
        sum += nums[i]
    }
    return sum
}
```

#### 对象 object

```typescript
let person = {
    name: '张三',
    age: 18,
    sayHi: function() {
        console.log('hi')
    }
}
```

##### 接口

TS 中的对象是结构化的，规定了对象有什么属性或方法

在使用对象前，可以根据需求，提前设计好对象的接口，约束对象的结构

```typescript
interface IPerson {
    name: string;
    age: number;
    sayHi: () => void;
}

let p1: IPerson = {
    name: '张三',
    age: 18,
    sayHi: function() {
        console.log('hello')
    }
}
```

> 注意：键值对中的值是类型
>
> 注意：多个键值对之间使用分号分隔（可以省略），不是逗号

###### 取值和赋值

```typescript
// 创建接口
interface IUser {
    name: string;
    height: number;
    sing: () => void;
}

// 创建对象
let jay: IUser = {
    name: '周杰伦',
    height: 175,
    sing: function() {
        console.log('故事的小黄花')
        console.log('我是', this.name)
    }
}

// 访问对象属性
console.log(jay.name)    // 周杰伦
console.log(jay.height)
// 修改对象属性
jay.name = '周董'
// 访问对象方法
jay.sing()               // 周董
```



## 1.2 类型推论

在 TS 中，某些没有明确指出类型的地方，类型推论会帮助提供类型

两种场景：1. 声明变量并初始化时 2. 决定函数返回值时

```typescript
let age: number(可以省略) = 18
let songName: string(可以省略) = '雅俗共赏'
let person: IUser(可以省略) = {
    name: 'jack'
}
function sum(num1: number, num2: number): number(可以省略) {
    return num1 + num2
}
```

## 1.3 类型断言

手动指定更加具体（精确）的类型，子类？

使用场景：当你比 TS 更了解某个值的类型，并且需要指定更加具体的类型时

```typescript
document.querySelector() // 返回类型为 Element
// 如果是 h1 标签
let title = document.querySelector('#title') as HTMLHeadingElement

// 如果是 img 标签
let img = document.querySelector('#img') as HTMLImageElement

// 如果不指定类型，不能访问标签特有属性
title.innerText = ''
img.src = '' 
```

> 可以通过 console.dir() 打印对象所有属性和方法

```typescript
// 1. 获取到所有的 p 元素列表
let list = document.querySelectorAll('.a')
// 2. 遍历 p 元素列表
list.forEach((item, index) => {
    // 3. 使用类型断言，指定 item 类型
    let p = item as HTMLParagraphElement
    // 4. 替换 innerText
    p.innerText = '[' + index + ']' + p.innerText
})

```



