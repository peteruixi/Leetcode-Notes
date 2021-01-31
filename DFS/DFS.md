# DFS

Combination:

``` python
Class Combination():
  nums = [....]
  ans = []
  # C(m,n)
  def dfs(n,s,cur):
    if len(cur) == n:
      ans.append(cur)
      return
    for i in range(s,len(nums)):
      cur.append(nums[i])
      dfs(n,i+1,cur)
      cur.pop()
  for i in range(len(nums)):
    dfs(i,0,[])

```

Permutation:

``` python
Class Permutation:
  nums = [....]
  ans = []
  used = [False]*len(nums)
  
  # P(m,n)
  def dfs(n,cur):
    if len(cur) == n:
      ans.append(cur)
      return
    for i in range(len(nums)):
      if used[i]:continue
      used[i] = True
      cur.append(nums[i])
      dfs(n,cur)
      cur.pop()
      used[i] = False
  for i in range(len(nums)):
    dfs(i,0,[])
```

