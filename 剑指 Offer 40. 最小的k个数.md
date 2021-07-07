### 剑指 Offer 40. 最小的k个数
* 输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4

> 输入：arr = [3,2,1], k = 2

> 输出：[1,2] 或者 [2,1]

```
//排序后返回切片
func getLeastNumbers(arr []int, k int) []int {
    if len(arr) < k {
        return nil
    }
    sort.Ints(arr)
    return arr[:k]
}
```

```
//几个排序算法的实现
func getLeastNumbers(arr []int, k int) []int {
    if len(arr) < k{
        return nil
    }
    quicksort(arr)
    return arr[:k]
}

//归并排序
func merge_sort(nums []int)  {
	n := len(nums)
	merge_sort_c(nums, 0, n-1)
}

func merge_sort_c(nums []int, p, r int)  {
	//递归终止
	if p >= r {
		return
	}

	q := (p + r) / 2
	merge_sort_c(nums, p, q)
	merge_sort_c(nums, q + 1, r)
	merge(nums, p, q, r)
}

func merge(nums []int, p , q, r int) {
	i, j := p, q+1
	var tmp = []int{}
	for i<=q && j<=r {
		if nums[i] <= nums[j]{
			tmp = append(tmp, nums[i])
			i ++
		} else {
			tmp = append(tmp, nums[j])
			j ++
		}
	}
	if i <= q {
		tmp = append(tmp, nums[i : q+1]...)
	}
	if j <= r {
		tmp = append(tmp, nums[j : r+1]...)
	}
	for pos, item := range tmp{
		nums[p + pos] = item
	}
}


//快速排序
func quicksort(nums []int) {
    n := len(nums)
    quicksort_c(nums, 0, n-1)
}
func quicksort_c(nums []int, p, r int) {
    if p >= r{
        return  
    } 
    q := partition(nums, p, r)
    quicksort_c(nums, p, q-1)
    quicksort_c(nums, q+1, r)
}

func partition(nums []int, p, r int) int {
    pivot := nums[r]
    i := p
    for j:=p; j<=r-1; j++{
        if nums[j] < pivot {
            nums[i], nums[j] = nums[j], nums[i]
            i ++
        }
    }
    nums[i], nums[r] = nums[r], nums[i]
    return i
}


//选择排序
func selectsort (nums []int) {
    n := len(nums)
    for i:=0; i<n-1; i++{
        index := i
        tmp := nums[i]
        for j:=i; j<n; j++{
            if nums[j] < tmp{
                index = j
                tmp = nums[j]
            }
        }
        nums[i], nums[index] = nums[index], nums[i]
    }
}

//冒泡排序
func maopaosort (arr []int) {
    n := len(arr)
    for i:=0; i<n; i++{
        isSwag := false
        for j:=0; j<n-i-1; j++{
            if arr[j] > arr[j+1]{
                arr[j], arr[j+1] = arr[j+1], arr[j]
                isSwag = true
            }
        }
        if(!isSwag) {
            break
        }
    }
}

//插入排序
func insertsort (arr []int) {
    n := len(arr)
    for i:=1; i<n; i++{
        tmp := arr[i]
        j:=i-1
        for ; j>=0; j--{
            if arr[j] > tmp {
                arr[j+1] = arr[j]
            } else {
                break
            }
        }
        arr[j+1] = tmp
    }
}
```
