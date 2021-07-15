### 剑指 Offer 58 - I. 翻转单词顺序

* 输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。为简单起见，标点符号和普通字母一样处理。例如输入字符串"I am a student. "，则输出"student. a am I"

> 输入: "the sky is blue"
> 输出: "blue is sky the"

```
func reverseWords(s string) string {
	strSlice := strings.Fields(s)
    left, right := 0, len(strSlice) - 1
    for left < right {
        strSlice[left], strSlice[right] = strSlice[right], strSlice[left]
        left ++ 
        right --
    }

    return strings.Join(strSlice, " ")
}
----------------------------------------------------------------------
func reverseWords(s string) string {
    var strs []string
    var fast int
    for fast < len(s) {
        var str string
        for fast < len(s) && s[fast] == ' ' {
            fast ++
        }

        for fast < len(s) && s[fast] != ' ' {
            str += string(s[fast])
            fast ++ 
        }

        if len(str) > 0 {
            strs = append(strs, str)
        }
    }

    for i:=0;i<len(strs)/2;i++{
        strs[i], strs[len(strs)-i-1] = strs[len(strs)-i-1], strs[i]
    }

    return strings.Join(strs, " ") 
}
```
