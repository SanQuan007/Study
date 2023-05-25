# template标签

Vue中提供了一个特殊标签 `<template>`,这是一个空标签，可以在任意的HTML标签中使用。

## 一、基础语法

1、`<template>`最终在浏览器解析完成后，并不会在页面的节点中渲染出来

### `<template>` 搭配 `v-for`

```html
<div>
    <template v-for="item in 3">
        <h1 :key="item">Hello</h1>
        <h1 :key="item + 'a'">你好</h1>
    </template>
</div>
```

注意：

1、v-for可以在template身上使用，但是key属性不能设置在template身上，需要设置在template内部的真实节点身上；

2、template内部真实节点的key属性之间，不能重复；

### `<template>` 搭配 `v-if`

```html
<div>
    <template v-if="true">
        <h1>hello</h1>
        <h1>你好</h1>
    </template>
</div>
```

注意：

1、 `v-show` 不能用在template身上。 

### `v-if` 和 `v-for`同时使用

**Vue官方不建议将`v-if` 和 `v-for`同时使用**，所以，我们也可以将其中一个指令添加到tamplate上

```html
<tbody>
                <template v-for="item in goods">
                    <tr v-if="item.count" :key="item.id">
                        <td>{{item.id}}</td>
                        <td>{{item.name}}</td>
                        <td>{{item.price}}</td>
                        <td>
                            <button @click="item.count--">-</button>
                            {{item.count}}
                            <button @click="item.count++">+</button>
                        </td>
                        <td>{{item.price * item.count}}</td>
                        <td><button @click="item.count = 0">删除</button></td>
                    </tr>
                </template>
            </tbody>
```

说明：

​	如果同时使用 `v-for`的优先级更高