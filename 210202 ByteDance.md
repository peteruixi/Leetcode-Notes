## 486

<img src="/Users/apple-5/Library/Application Support/typora-user-images/image-20210203153032806.png" alt="image-20210203153032806" style="zoom:50%;" />

题意是两名玩家依次从一个数组中抽牌 每次抽牌只能选数组两端的数字, 然后最后返回玩家1是否抽到最大的数. 若是两方所得相等, 也判为玩家1胜利.

### Code

##### Recursion

``` Python
def PredictTheWinner(self, nums: List[int]) -> bool:
         return self.getResult(nums, 0, len(nums)-1)>=0
    
    def getResult(self,nums,leftBount,rightBount):
        if leftBount == rightBount: 
            return nums[leftBount]
        return max(nums[leftBount]+self.getResult(nums,leftBount+1,rightBount),
                   nums[rightBount]+self.getResult(nums,leftBount,rightBount-1))
```

##### Dynamic Programming

```Python
def PredictTheWinner(self, nums: List[int]) -> bool:
        n = len(nums)
        dp = [[0]*n for _ in range(n)]
      
        # Filling the diagonal
        for key, value in enumerate(nums):
            dp[key][key]=value
        
        # Dynamic Programming
        for i in range(n-2,-1,-1):
            for j in range(i,n,1):
                dp[i][j] = max(nums[i] - dp[i+1][j], nums[j] - dp[i][j-1])
        print(dp)
        return True if dp[0][-1]>=0 else False
```

### Approach

> I think understaning the logic of recursion helps with the implementation of DP, understand the base case and the subproblem will help constructing the transition matrix. In previous problems, I have seemed to neglet this matter. What dynamic programming has allowed us, is the ability to save the overhead from repeated execution. The extra repeated computation time and space was saved by storing the previous computed results that could be reuse in future computation. 

Here for recursion the recursion tree is illustrated as follow:

![image-20210203173318058](/Users/apple-5/Library/Application Support/typora-user-images/image-20210203173318058.png)
In the graph, it shows the recursion scenarion at each stages. To begin with the original array `[1,5,233,7]`, there are two possible action for players, take the left most value or take the right most value. Like the graph shows, `[1,5,233,7]`becomes `[5,233,7]` or `[1,5,233]` at the next level of recursion. 

The rule of the game seems fairly straight forward, but how to we get our return value? how to we keep hold of the status at each phase? Since we are finding if player 1 wins , what we could store would be the winning score of player 1 at each stage,

> I had a question during this, why cant we do True and False like before, I do believe we are able to do that, once there is a way to figure out the relationship with the max function

Storing the difference between the two is more intuitive comparing. The graph above have lead us to the transition function where 

$$
DP [i] [j] = max( nums[left bound] + dp [left bound +1] [right bound],

nums[right bound] + dp [left bound] [right bound -1])
$$

| [1,5,233,7] | 0     | 1              | 2                    | 3                     |
| ----------- | ----- | -------------- | -------------------- | --------------------- |
| 0           | **1** | 1-5 vs 5-1 = 4 | 1-228 vs 233-4 = 229 | 1+221 vs 7-229 = 222  |
| 1           |       | **5**          | 5-233 vs 233-5 = 228 | 7-228 vs 5-226 = -221 |
| 2           |       |                | **233**              | 233-7 vs 7-233 = 226  |
| 3           |       |                |                      | **7**                 |

The DP array is initialized as table above. Since when the right most border and the left most border are the same the greatest different a player could generate would the value itself.  We are iterating from boto

### Complexity

- Time Complexity: $ O(N^2) , N is the length of array$ 
- Space Complexity:  $ O (N^2), N is the length of array $



## 85

## 84

## 60 

## 753. 破解保险箱

康托展开 - 排列组合 直接映射到相对的位置上, 能够完成1-1对立的哈希