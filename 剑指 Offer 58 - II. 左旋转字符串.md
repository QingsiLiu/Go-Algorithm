### 剑指 Offer 58 - II. 左旋转字符串

* 字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"

> 输入: s = "abcdefg", k = 2

> 输出: "cdefgab"

```
func reverseLeftWords(s string, n int) string {
    str := []rune(s)
    reverse(str[:n])
    reverse(str[n:])
    reverse(str)
    return string(str)
}

func reverse(str []rune) {
    i, j := 0, len(str) - 1
    for i < j {
        str[i], str[j] = str[j], str[i]
        i++
        j--
    }
}
--------------------------------------------------
func reverseLeftWords(s string, n int) string {
    l := len(s)
    str := []rune(s)
    // *需要判断所有字符都移动过了即可
    // 第二种方法是直接重复l和n的最大公约数次，涉及到数学证明，即线代中旋转归纳的旁系数
    counter := 0
    for i := 0; counter != l; i++ {
        t := str[i]
        for j := (i + n) % l; j != i; j = (j + n) % l {
            str[(j - n + l) % l] = str[j]
            counter++
        } 
        str[(i - n + l) % l] = t
        counter++
    }
    return string(str)
}

```
