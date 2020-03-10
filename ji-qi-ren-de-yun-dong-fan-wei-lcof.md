# 机器人的运动范围
> 地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

## BFS
(0,0) --------
 |
 |
 |
 |
 -----------(m-1,n-1)

```c++
int movingCount(int m, int n, int k) {
    // 已遍历节点
    vector<vector<bool>> pb(m, vector<bool>(n, false));
    // 经典队列
    queue<pair<int, int>> q;
    q.push({0,0});
    int res = 0;
    while (!q.empty())
    {
        // 出队
        auto t = q.front();
        q.pop();
        int x = t.first, y = t.second;
        // 截止条件
        if (x < 0 || x >= m || y < 0 || y >= n || pb[x][y] || (x % 10 + x / 10 + y % 10 + y / 10) > k)
            continue;
        // 通过节点
        pb[x][y] = true;
        res++;
        // 候选节点入队
        q.push({x + 1, y});
        q.push({x, y + 1});
    }
    return res;
}
```