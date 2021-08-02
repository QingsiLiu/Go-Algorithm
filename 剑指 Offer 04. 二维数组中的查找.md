### 剑指 Offer 04. 二维数组中的查找

* 在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数

```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。
给定 target = 20，返回 false。
```

```
func findNumberIn2DArray(matrix [][]int, target int) bool {
	m := len(matrix)
	if m < 1 {
		return false
	}

	n := len(matrix[0])
	if n < 1 || matrix[m-1][n-1] < target {
		return false
	}

    if matrix[0][0] > target {
        return false
    }
    
    for i := 0; i < m; i++{
        if target < matrix[i][0] {
			return false
		}
        for j := 0; j < n; j++{
            if target < matrix[i][j] || target > matrix[i][n-1]{
                break
            }
            if matrix[i][j] == target{
                return true
            }
        }
    }
    return false
}
```
