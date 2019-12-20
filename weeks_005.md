# ARTS

极客时间《左耳听风》专栏ARTS活动周打卡：

1. Algorithm: 每周至少做一道LeetCode算法题

2. Review: 阅读并点评至少一篇英文技术文章

3. Tip: 学习至少一个技术技巧

4. Share: 分享一篇有观点和思考的技术文章

## Algorithm

### 重建二叉树

```html
输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。
```

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function reConstructBinaryTree(pre, vin) {
  // write code here
  if (!pre.length || !vin.length) return null
  let index = vin.indexOf(pre[0])
  return {
    val: pre[0],
    left: reConstructBinaryTree(pre.slice(1, index + 1), vin.slice(0, index)),
    right: reConstructBinaryTree(pre.slice(index + 1), vin.slice(index + 1))
  }
}
```

## Review

这个太难以后再说...

## Tip

为了提升动画效果，浏览器在动画进行时的每一帧中都会重新绘制整个页面，这就造成了不必要的性能浪费。

GraphicsLayer 图像层是一个合成层，把需要进行动画的元素包含在这个合成层中，动画的每一帧就只会重新绘制这个合成层而不是整个页面了:

```css
transform: translate3d();
```

## Share

总结入行四年半大方向上的错误选择，[传送门](https://juejin.im/post/5dea06cf6fb9a0166049821a)
