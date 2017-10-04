# LeetCode

1. 进入 https://leetcode.com/，注册。
2. 进入 https://leetcode.com/problemset/all/，开始刷题。

1. Two Sum

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for (let i = 0; i < nums.length - 1; i++) {
            for (let j = i + 1; i < nums.length; j++) {
                if (nums[i] + nums[j] === target) {
                    return [i, j]
                }
            }
        }
};
```

### 7. Reverse Integer



