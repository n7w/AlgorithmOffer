# 二维数组中的查找

> 在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
```py
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
```

## 二叉搜索树法
右上角是树的顶点，左边为小，右边（下边）为大
```c++
bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) {
    if(!matrix.size() || !matrix[0].size()) 
        return false;
    
    int row = 0, col = matrix[0].size() - 1;
    
    while(row < matrix.size() && col > -1) {
        if(matrix[row][col] == target)
            return true;
        else if(matrix[row][col] > target) 
            col--;
        else 
            row++;
    }
    return false;
}
```