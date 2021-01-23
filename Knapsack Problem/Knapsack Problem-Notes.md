# Knapsack Problem Notes

**常见的背包问题有:**

**1、组合问题**

 `dp[i] += dp[i-num]`

[377. 组合总和 Ⅳ](https://leetcode-cn.com/problems/combination-sum-iv/description/)
[494. 目标和](https://leetcode-cn.com/problems/target-sum/description/)
[518. 零钱兑换 II](https://leetcode-cn.com/problems/coin-change-2/description/)

**2、True、False问题 **

 `dp[i] = dp [i] or dp[i-num]`

[139. 单词拆分](https://leetcode-cn.com/problems/word-break/)
[416. 分割等和子集](https://leetcode-cn.com/problems/partition-equal-subset-sum/description/)

**3、最大最小问题 **

 `dp[i] = min(dp[i], dp[i-num]+1`**或者** `dp[i] = max(dp[i], dp[i-num]+1)`

[474. 一和零](https://leetcode-cn.com/problems/ones-and-zeroes/description/)
[322. 零钱兑换](https://leetcode-cn.com/problems/coin-change/description/)

## 解题思路

1.分析是否为背包问题。
2.是以上三种背包问题中的哪一种。
3.是0-1背包问题还是完全背包问题。也就是题目给的nums数组中的元素是否可以重复使用。
4.如果是组合问题，是否需要考虑元素之间的顺序。需要考虑顺序有顺序的解法，不需要考虑顺序又有对应的解法。

## 背包问题技巧

1. 0-1 背包, 数组中的元素不可重复使用. nums放在外循环,target放在内循环,且内循环倒序

``` Python
for num in nums:
  for i in range(target, nums-1,-1)
```



1. 完全背包, 数组中的元素可重复使用,nums放在外循环,target 在内循环.且内虚幻正序:

   ``` Python
   for num in nums:
     for i in range(nums, target+1): 
   ```

   

2. 排列问题, 需考虑元素之间的顺序, 需将target放在外循环,将nums放在内循环:

   ```python
   for i in rage(1,target+1):
     for num in nums:
   ```

   

