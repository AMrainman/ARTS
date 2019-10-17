## Algorithm

### 两数之和

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9

所以返回 [0, 1]
```

1. [我的解答](https://leetcode-cn.com/submissions/detail/32689224/)：

```js
var twoSum = function(nums, target) {
    for (let i = 0; i < nums.length; i++) {
        let n = nums[i]
        let m = target - n
        if (nums.includes(m)) {
            let x = nums.indexOf(m);
            if (x !== i) {
                return [i, x]
            }
        }
    }
    return null
};
```

2. 大神答案

```js
var twoSum = function(nums, target) {
    var map = new Map();
    for (var i = 0; i < nums.length; i++) {
        var part = target - nums[i];
        if (map.has(part) && map.get(part) !== i) return [i, map.get(part)]    // 避免重复利用同一个元素 
        map.set(nums[i], i)
    }
};
```

利用 Map 结构巧妙将复杂度降到了O(n)，太神奇了~

## Review

## Tip

怎么做出图片倒影？无论图片大小变化都不用调整代码的~效果如下：

![](https://camo.githubusercontent.com/65209be23b936b4f648981bc8836601d6d6cde35/687474703a2f2f696d616765732e636e626c6f67732e636f6d2f636e626c6f67735f636f6d2f636f636f31732f3838313631342f6f5f636f70792e706e67)

刚看题目我一时懵逼，不知所措~

方法一：

```css
div{
    -webkit-box-reflect: below; // below | above | left | right 代表下上左右   -webkit- 内核的浏览器才支持
}
```

方法二：

```css
div::after {
    content: "";
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    bottom: -100%;
    background-image: inherit; // 利用图片继承，这一般人想不到吧...
    transform: rotateX(180deg);
}
```

## Share

新学习了 Grid 网格布局，[文章链接](https://juejin.im/post/5da1749cf265da5b86013198)
