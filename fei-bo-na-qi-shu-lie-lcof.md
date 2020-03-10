# 斐波那契数列

>写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项。斐波那契数列的定义如下
```
F(0) = 0,   F(1) = 1  
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
```

## 递归
```c++
int fib(int n) {
    if(n <= 1) return n;
    return fib(n-1) + fib(n-2);
}
```

## 动态规划
自底而下
```c++
int fib(int n) {
    int fn_2 = 0, fn_1 = 1, fn;
    while(n--) {
        fn = fn_1 + fn_2
        fn_2 = fn_1;
        fn_1 = fn;
    }
    return fn_2;
}
```