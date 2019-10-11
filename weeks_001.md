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


## Review

## Tip

## Share
