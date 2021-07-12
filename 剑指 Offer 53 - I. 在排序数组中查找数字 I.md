### 剑指 Offer 53 - I. 在排序数组中查找数字 I

* 统计一个数字在排序数组中出现的次数。

> 输入: nums = [5,7,7,8,8,10], target = 8

> 输出: 2

```
func search(nums []int, target int) int {
    l := help(nums, 0, len(nums)-1, target)
    r := help(nums, l, len(nums)-1, target+1)
    return r-l
}

func help(nums []int, l, r, target int) int {
    for l <= r {
        mid := l + ((r-l) >> 1)
        if nums[mid] < target {
            l = mid + 1
        } else {
            r = mid - 1
        }
    }
    return l
}

------------------------------------------------

func search(nums []int, target int) int {
    if len(nums) == 0 {
        return 0
    }
    n := len(nums)
    l, r := 0, n-1
    var lres, rres int
    for l <= r {
        mid := l + ((r-l) >> 1)
        if nums[mid] >= target {
            r = mid - 1
        } else {
            l = mid + 1
        }
    }

    if l < n && nums[l] == target {
        lres = l
    } else {
        return 0
    }

    l, r = 0, n-1
    for l <= r {
        mid := l + ((r-l) >> 1)
        if nums[mid] > target {
            r = mid - 1
        } else if nums[mid] < target {
            l = mid + 1
        } else {
            if mid == n-1 || nums[mid+1] != target {
                rres = mid
                break
            } else {
                l = mid + 1 
            }
        }
    }

    return rres-lres+1
}
```
