## Algorithm

### 二维数组查找

> 在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

比如二维数组：[[1, 2, 3, 4, 5], [6, 7, 8, 9, 10], [11, 12, 13, 14, 15]]

思路：由于数组是从左往右，从上往下递增的，所以我们从左下角开始查找，大了往右，小了往左：

```js
const find = function (nums, target) {
  let rowLen = nums[0].length
  let colLen = nums.length
  if (rowLen < 1 || colLen < 1) return false
  let row = rowLen - 1
  let col = 0
  while (col <= colLen - 1 && row >= 0) {
    let current = nums[row][col]
    if (current < target) {
      row--
    } else if (current > target) {
      col++
    } else {
      return true
    }
  }
  return false
}
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

新学习了 Grid 网格布局，[文章链接](https://juejin.im/post/5da1749cf265da5b86013198)
