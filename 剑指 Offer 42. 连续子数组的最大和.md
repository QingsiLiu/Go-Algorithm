### 剑指 Offer 42. 连续子数组的最大和
* 输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

> 输入: nums = [-2,1,-3,4,-1,2,1,-5,4]

> 输出: 6

```
//动态规划
dp[i]是以i结尾的数组最大和
func maxSubArray(nums []int) int {
    dp := make([]int, len(nums))
    for i, _ := range dp {
        dp[i] = nums[i]
    }
    for i:=1; i<len(dp); i++{
        if dp[i]+dp[i-1] > dp[i] {
            dp[i] = dp[i]+dp[i-1]
        }
    }
    res := dp[0]
    for i, _ := range dp {
        if dp[i] > res {
            res = dp[i]
        }
    }
    return res
}

//暴力遍历法，直接超时...
func maxSubArray(nums []int) int {
	n := len(nums)
	if n == 0 {
		return 0
	}
	if n == 1 {
		return nums[0]
	}
	res := nums[0]
	for i:=0; i<n-1; i++{
		var tmp_sum = nums[0]
		for j:=i; j<n; j++{
			tmp_sum = sum_nums(nums[i:j]) + nums[j]
			res = max(tmp_sum, res)
		}
	}

	res = max(res, nums[n-1])
	return res
}

func max(x, y int) int {
	if (x > y){
		return x
	}
	return y
}

func sum_nums(nums []int) (sum int) {
	for i:=0; i<len(nums); i++{
		sum += nums[i]
	}
	return
}
```
