# 从尾到头打印链表
> 输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

## 翻转链表
```c++
vector<int> reversePrint(ListNode* head) {
    vector<int> list, res;
    while (head)
    {
        list.push_back(head->val);
        head = head->next;
    }
    for (int i = list.size() - 1; i > -1; i--)
    {
        res.push_back(list[i]);
    }
    return res;
}
```

## 翻转数组or用栈
```c++
vector<int> reversePrint(ListNode* head) {
    stack<int> s;
    vector<int> v;
    while(head) {
        s.push(head->val);
        head = head->next;
    }
    while(!s.empty()) {
        v.push_back(s.top());
        s.pop();
    }
    return v;
}
```

## 递归
```c++
vector<int> res;
vector<int> reversePrint(ListNode* head) {
    if(head == NULL) return res;
    reversePrint(head->next);
    res.push_back(head->val);
    return res;
}
```