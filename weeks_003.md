# ARTS

极客时间《左耳听风》专栏ARTS活动周打卡：

1. Algorithm: 每周至少做一道LeetCode算法题

2. Review: 阅读并点评至少一篇英文技术文章

3. Tip: 学习至少一个技术技巧

4. Share: 分享一篇有观点和思考的技术文章

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

css 使用 <img> 实现背景图片的 `cover` 等效果：

```html
<img src="https://user-gold-cdn.xitu.io/2019/11/2/16e2b3bc72d4b202?imageView2/1/w/1304/h/734/q/85/format/webp/interlace/1">
<style>
  img {
    width: 200px;
    height: 50px;
    object-fit: cover;
  }
</style>
```

额，这次 tip 有点凑合，下次好好努力~~

## Share

本期主要学习了CSS的继承，[文章链接](https://juejin.im/post/5dcb89186fb9a04a752ba034)
