## Algorithm

### 替换空格

> 请实现一个函数，将一个字符串中的空格替换成“%20”。

例如，当字符串为 `We Are  Happy` ，则经过替换之后的字符串为 `We%20Are%20%20Happy` 。

思路1：正则

```js
let str = 'We Are  Happy'
str = str.replace(/\s/g, '%20')
```
思路2：递归

```js
let str = 'We Are  Happy'
const fn = (str, symbol) => {
  let i = str.indexOf(' ')
  if (~i) {
    str = str.replace(/\s/, symbol)
    return fn(str, symbol)
  } else {
    return str
  }
}
str = fn(str, '%20')
```

思路3：map

```js
let str = 'We Are  Happy'
const fn = (str, symbol) => {
  let arr = str.split('')
  return arr.map(item => {
    if (item === ' ') {
      return '%20'
    } else {
      return item
    }
  }).join('')
}
str = fn(str, '%20')
```

## Review

这个太难以后再说...

## Tip

谈谈 CSS 关键字 initial、inherit 和 unset

## Share

本期主要学习了CSS的继承，[文章链接](https://juejin.im/post/5dcb89186fb9a04a752ba034)
