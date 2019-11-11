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

最近要做一个这样的效果：

![](https://user-gold-cdn.xitu.io/2019/8/20/16cae04e03f3c6d1?imageslim)

参考大佬的方法通过 `max-height` 定义收起的最小高度和展开的最大高度，设置两者间的过渡切换。起初总觉得怪怪的，展开和折叠的过渡之间好像有延迟并不是同步进行的，理想状态下展开和折叠应该是同时发生同时完成的。于是把过渡时间调大，发现果真有延迟：[地址](http://js.jirengu.com/qazum/1/edit?html,css,output)。

起初以为是浏览器的渲染问题，导致两个过渡效果不能同时进行，也怀疑可能是 hover 离开时有延迟，但很快就被打脸了：[地址](http://js.jirengu.com/qariy/2/edit?html,css,output)。

就这样漫无目的的调试了几天（有空就看下，并没一直看），都没有发现问题的所在。

今天突然想到我在 `hover` 的时候设置的 `max-height` 过大了，而正是因为这个 `max-height` 比实际高度大，导致了过渡效果在渲染的时候会计算从 `600px` 到 `0px` 的时间，而不是从实际高度 `120px` 到 `0px` 的时间。

```
展开：0 ===> 120 --------> 600
折叠：600 --------> 120 ===> 0
```

可以看出，展开的时候从 `120` 到 `600` 和折叠的时候从 `600` 到 `120` 这段时间，页面效果其实是没有变化的，而展开和折叠的高度变化正好是相反的，这就产生了时间差，导致每次折叠的时候刚开始页面都没有变化，当高度到了 `120` 才开始有过渡效果。

所以只需要设置正确的 `max-height` 就可以产生完美的过度效果了：[地址](http://js.jirengu.com/qidoh/3/edit?html,css,output)

## Share

本期主要学习了函数式编程，[文章链接](https://juejin.im/post/5d5c92db51882505750d69b1)
