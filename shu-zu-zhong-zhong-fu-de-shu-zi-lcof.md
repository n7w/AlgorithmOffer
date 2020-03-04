# 数组中重复的数字

>在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

## 排序法
排好序后找到重复元素即可
```c++
int main(vector<int> nums) {
    sort(nums);
    for(int i = 1; i < nums.size(); ++i) {
        if(nums[i-1] == nums[i]) return nums[i];
    }
    return -1;
}        
```

## 集合（哈希表也行）
用集合保证元素唯一
```c++
int main(vector<int> nums) {
    unordered_set <int> s;
    for(auto num : nums) {
        if(!s.insert(num)) return num;
    }
    return -1;
}
```

## 指针+原地排序
索引`index`是唯一的，利用指针相遇的思想遍历数组（龟兔赛跑）  
也可以想成索引唯一映射
```c++
int findRepeatNumber(vector<int>& nums) {
    for(int i = 0; i < nums.size(); ++i) {
        if(nums[i] != i) {
            if(nums[i] == nums[nums[i]]) 
                return nums[i];
            // swap
            nums[i] ^= nums[nums[i]];
            nums[nums[i]] ^= nums[i];
            nums[i] ^= nums[nums[i]];            
        }
    }
    return -1;
}
```