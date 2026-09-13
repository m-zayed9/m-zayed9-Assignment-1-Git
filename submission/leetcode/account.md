https://leetcode.com/u/zayed_98/

## LeetCode 1. Two Sum

Link : https://leetcode.com/problems/two-sum


```typescript
function twoSum(nums: number[], target: number): number[] {
    for (let i = 0; i < nums.length; i += 1) {
        for (let j = i + 1; j < nums.length; j += 1) {
            if (nums[i] + nums[j] === target) {
                return [i, j];
            }
        }
    }

    return [];
}
```