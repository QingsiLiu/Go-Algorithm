### 剑指 Offer 13. 机器人的运动范围

* 地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。
* 例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

> 输入：m = 2, n = 3, k = 1

> 输出：3

```
func movingCount(m int, n int, k int) int {
    var dfs func(y, x int) (res int)

    visited := make(map[string]bool)

    digitsum := func(x int) (res int) {
        for ; x>0; x/=10 {
            res += x%10
        }
        return 
    }

    dfs = func(y, x int) (res int) {
        if y < 0 || y > m-1 {
            return
        }
        if x < 0 || x > n-1 {
            return 
        } 

        if _, isExist := visited[fmt.Sprintf("%d,%d", y, x)]; isExist {
            return
        }

        if (digitsum(y) + digitsum(x)) > k {
            return
        }

        visited[fmt.Sprintf("%d,%d", y, x)] = true
        res += 1

        res += dfs(y, x+1)
        res += dfs(y+1, x)
        return 
    }

    return dfs(0, 0)
}
```


 











