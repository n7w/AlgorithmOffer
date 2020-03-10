# 旋转数组的最小数字

> 把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

## 二分法
原有序数组，可用二分法找到上分界和下分界  
即 `upper_bound()` 和 `lower_bound()`
```c++
int minArray(vector<int>& numbers) {
    int low = 0, high = numbers.size() - 1, mid = 0;
    while (low < high)
    {
        mid = low + (high - low) / 2;
        if (numbers[mid] > numbers[high])
            low = mid + 1; // mid 落在原数组部分
        else if (numbers[mid] < numbers[high])
            high = mid; // mid 落在旋转数组部分
        else
            high--; 
            // 出现重复值，但目标是唯一最小值，numbers[high] 所在的必然是旋转数组，故移动high
    }
    return numbers[low];
```