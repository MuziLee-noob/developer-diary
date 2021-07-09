# TypeScript概述

## 1.1 TypeScript 是什么

TypeScript 是 JavaScript 的超集，TypeScript = Type + JavaScript

TypeScript 是微软开发的开源编程语言，设计目标是开发大型应用。可以在任何浏览器、计算机、操作系统上运行

```typescript
// TS 有明确的数据类型，number
let age: number = 18
// JS 无明确的数据类型
let age = 18
```

## 1.2 TS 的优势

- 类型化思维方式，使得开发更加严谨，提前发现错误
- 提高了代码可读性，使维护和重构代码更容易
- 补充了接口、枚举等开发大型应用时 JS 缺失的功能
- Vue 3 使用 TS

## 1.3 安装运行ts文件

```
npm i -g typescript

tsc hello.ts // 编译成js

node hello.js
```

简化执行 TS 的步骤

```
npm i -g tsc-node

tsc-node hello.ts
```

