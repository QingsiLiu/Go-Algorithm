### 剑指 Offer 50. 第一个只出现一次的字符

* 在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母

> s = "abaccdeff"

> 返回 "b"

```
func firstUniqChar(s string) byte {
    if len(s) == 0 {
        return ' '
    }
    tmp := [26]int{}
    for i:=0; i<len(s); i++{
        tmp[s[i]-'a']++
    }
    for i:=0; i<len(s); i++{
        if tmp[s[i]-'a'] == 1 {
            return s[i]
        }
    }
    return ' '
}
```
