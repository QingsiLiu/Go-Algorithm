### 剑指 Offer 39. 数组中出现次数超过一半的数字

* 数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。
   * 你可以假设数组是非空的，并且给定的数组总是存在多数元素

> 输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]

> 输出: 2

```
//排序后遍历计数法
func majorityElement(nums []int) int {
    if len(nums) == 1 {
        return nums[0]
    }
    val := len(nums) / 2
    sort.Ints(nums)
    count := 1
    for i := 0; i < len(nums)-1; i ++ {
        if nums[i] == nums[i+1] {
            count ++
            if count > val {
                return nums[i]
            }
        } else {
            count = 1
        }
    }
    return 0
}
//字典映射
func majorityElement(nums []int) int {
    if len(nums) == 1 {
        return nums[0]
    }
    val := len(nums) / 2
    m := map[int]int{}
    for _, v := range nums {
        m[v]++
    }
    for k, v := range m {
        if v > val {
            return k
        }
    }
    return 0
}
//加减法
func majorityElement(nums []int) int {
    tmp := 0
    v := nums[0]
    for _, val := range nums {
        if tmp == 0 {
            v = val
        }
        if val == v {
            tmp ++
        } else {
            tmp --
        }
    }
    return v
}
```
