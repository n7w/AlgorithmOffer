# 从上到下打印二叉树
```py
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7

按照之字形顺序打印二叉树,即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推：
[
  [3],
  [20,9],
  [15,7]
]
```

## 经典BFS
```c++
vector<vector<int>> levelOrder(TreeNode* root) {
    vector<vector<int>> res;
    queue<TreeNode *> q;
    if (!root)
        return res;
    q.push(root);
    while (!q.empty())
    {
        vector<int> sub;
        for (int i = q.size(); i; i--)
        {
            if (q.front()->left)
                q.push(q.front()->left);
            if (q.front()->right)
                q.push(q.front()->right);
            sub.push_back(q.front()->val);
            q.pop();
        }
        if ((res.size() & 1) == 1)
            reverse(sub.begin(), sub.end());
        res.push_back(sub);
    }
    return res;
}
```