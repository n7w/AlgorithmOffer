# 替换空格
> 请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

## 正则表达式
```py
def main(str):
    return str.replace(" ", "%20")
```

## 新建字符串
像Java这种给了`String`却又不能修改就只能造新字符串了
```c++
string replaceSpace(string s) {
    string res = "";
    for(int i = 0; i < s.size(); ++i) {
        if(s[i] == ' ') res += "%20";
        else res += s[i];
    }
    return res;
}
```

## 原字符串修改
统计空格数，从后向前遍历
```c++
void replaceSpace(char *str,int length) {
    int space = 0;
    for (int i = 0; i < length; ++i) {
        if (str[i] == ' ')  space++;
    }
    for (int i = length - 1; i > -1; i--) {
        if (str[i] == ' ') {
            str[i + space * 2] = '0';
            str[i + space * 2 - 1] = '2';
            str[i + space * 2 - 2] = '%';
            space--;
        }
        else str[i + space * 2] = str[i];
    }
}
```