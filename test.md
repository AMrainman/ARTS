# ARTS

极客时间《左耳听风》专栏ARTS活动周打卡：

1. Algorithm: 每周至少做一道LeetCode算法题

2. Review: 阅读并点评至少一篇英文技术文章

3. Tip: 学习至少一个技术技巧

4. Share: 分享一篇有观点和思考的技术文章

## Algorithm

### 两个栈来实现一个队列

```html
题目描述
用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。（这题虽然实现很简单，但是逻辑还是有点绕的）
```

```js
let arr1 = []
let arr2 = []
function push(node) {
  arr1.push(node)
}
function pop() {
  if (!arr2.length) {
    while (arr1.length) {
      arr2.push(arr1.pop())
    }
  }
  return  arr2.pop()
}
```

## Review

这个太难以后再说...1234

## Tip
阿斯蒂芬
## Share

