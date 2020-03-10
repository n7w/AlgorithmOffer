# 第一个只出现一次的字符
> 在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。

## 经典映射
```c++
char firstUniqChar(string s) {
    int ascii[128] = {0};
    for(auto c : s) ascii[c]++;
    for(auto c : s) {
        if(ascii[c] == 1) return c;
    }
    return ' ';
}
```