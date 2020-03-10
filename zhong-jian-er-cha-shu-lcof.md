# 重建二叉树
> 输入某二叉树的前序遍历和中序遍历的结果，请重建该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

## 找规律+递归
 中序遍历中 root 的位置为 i, [start....i - 1] 为中序遍历中的左子树，[i+1 ... end]为中序遍历中的右子树  
 start ... i-1 为左子树的长度， i+1 .... end 为右子树的长度  
对应前序遍历中 root + 1 为左子树的根节点， root + 1 + i - start 为右子树的根节点
```c++
TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
    return build(preorder, inorder, 0, 0, preorder.size()-1);
}

TreeNode* build(vector<int>& preorder, vector<int>& inorder, int root, int start, int end) {
    // 截止条件
    if(start > end) return NULL;
    // 合格节点
    TreeNode *tree = new TreeNode(preorder[root]);
    // 按规律
    int i = start;
    while(i < end && preorder[root] != inorder[i]) i++;
    // 递归
    tree->left = build(preorder, inorder, root + 1, start, i - 1);
    tree->right = build(preorder, inorder, root + 1 + i - start, i + 1, end);
    // 递归结束
    return tree;    
}
```