# ARTS

极客时间《左耳听风》专栏ARTS活动周打卡：

1. Algorithm: 每周至少做一道LeetCode算法题

2. Review: 阅读并点评至少一篇英文技术文章

3. Tip: 学习至少一个技术技巧

4. Share: 分享一篇有观点和思考的技术文章

## Algorithm

### 从尾到头打印链表

```html
输入一个链表，按链表从尾到头的顺序返回一个ArrayList。
```

1. 数组

```js
function mapLinkedList(head) {
  let current = head
  let arr = []
  while (current) {
    arr.unshift(current.element)
    current = current.next
  }
  return arr
}
```

经测试 `unshift` 性能比 `push reverse` 好，可能是 js 底层对 `unshift` 做过优化处理~~

2. 递归

```js
function mapLinkedList(current, arr = []) {
  if (!current) return [] // 忘加这个边界判断导致浪费了很多时间~~
  arr.unshift(current.element)
  current = current.next
  if (current) {
    return mapLinkedList(current, arr)
  } else {
    return arr
  }
}
```

## Review

这个太难以后再说...

## Tip

1. 文字渐变色实现

```html
<i class="iconfont iconfontBeautifulGril"></i>
<style>
  i {
    color: transparent;
    -webkit-background-clip: text;
    background-image: linear-gradient(122deg, #f3e0c4 0%, #c6a56b 100%);
  }
</style>
```

2. 导航条hover跟随效果：[地址](http://js.jirengu.com/doxoz/1/edit?html,css,output)

```html
<ul>
  <li>百度</li>
  <li>阿里</li>
  <li>腾讯</li>
  <li>字节跳动</li>
</ul>
<style>
ul {
  display: flex;
  text-align: center;
  border-bottom: 1px solid lightblue;
}
li {
  position: relative;
  flex: 1;
  height: 40px;
  line-height: 40px;
}
li:before {
  content: '';
  position: absolute;
  left: 100%;
  right: 0;
  top: 100%;
  width: 0;
  height: 4px;
  background: cyan;
  transition: all 300ms;
}
li:hover:before {
  left: 0;
  right: 0;
  width: 100%;
}
li:hover + li:before {
  left: 0;
  right: 0;
}
</style>
```

## Share

这两周周实在写不出来，先欠着吧~~

接下来两三周只进行tips和算法。
