---
title: JavaScript实现range函数
tags: [随笔, 代码]
date: 2018-06-08 21:47:01
---

会生成一个可迭代对象，就像Python中的那样
<!--more-->
```js
/**
 * 生成迭代器
 *
 * @param {Number} start 开始值
 * @param {Number} end 结束值
 * @param {Number} [step=1] 步长
 * @returns {Generator} 迭代器
 */
function* range(start, end, step = 1) {
    if (undefined === end) {
        [end, start] = [start, 0]
    }
    if (start < end) {
        for (let i of Array(Math.ceil((end - start) / step)).keys()) {
            yield i * step + start
        }
    } else {
        return []
    }
}
```
此函数在JavaScript中实现了python中的range函数，  
想要使用python中的for…in结构可以这样做：
```js
for (let i of range(10)){
    // code
}
```
想要返回输出数组可以这样做：
```js
[...range(10)]
```