### 剑指 Offer 57. 和为s的两个数字

```
func twoSum(nums []int, target int) []int {
    m := map[int]int{}

    for i, x := range nums {
        if _, ok := m[target-x]; ok {
            return []int{x, target-x}
        }
        m[x] = i
    }

    return nil
}
------------------------------------------------------
func twoSum(nums []int, target int) []int {
    left, right := 0, len(nums)-1
    for left < right {
        sum := nums[left] + nums[right]
        if sum == target {
            return []int{nums[left], nums[right]}
        } else if sum > target{
            right --
        } else {
            left ++
        }
    }
    return nil
}
```
