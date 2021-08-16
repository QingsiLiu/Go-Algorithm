### 剑指 Offer 14- I. 剪绳子

```
func cuttingRope(n int) int {
    dp := make([]int, n+1)
    dp[0], dp[1], dp[2] = 0, 1, 1
    var tmp1, tmp2 int
    for i := 3; i<n+1; i++ {
        dp[i] = dp[i-1]
        for j :=1; j<=i/2; j++ {
            tmp1 = max(dp[j], j)
            tmp2 = max(dp[i-j], i-j)
            dp[i] = max(dp[i], tmp1*tmp2)
        }
    }
    
    return dp[n]
}

func max(i, j int) int {
    if i > j {
        return i
    }
    return j
}
```
