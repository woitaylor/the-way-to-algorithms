# the-way-to-algorithms

### 二分查找法 ###
二分查找法是指在** 有序 **的数组中查找目标值target:

#### 目标 ####
理解区间（范围）的重要性：

C++实现代码：
```
template<typename T>
int binarySearch(T arr[], int n, T target){

    int l = 0, r = n - 1; // 在[l...r]的范围里寻找target
    while(l <= r){    // 当 l == r时,区间[l...r]依然是有效的
        int mid = l + (r - l) / 2;
        if(arr[mid] == target) return mid;
        if(target > arr[mid])
            l = mid + 1;  // target在[mid+1...r]中; [l...mid]一定没有target
        else    // target < arr[mid]
            r = mid - 1;  // target在[l...mid-1]中; [mid...r]一定没有target
    }

    return -1;
}

```

下面是修改了区间后的代码：
```
template<typename T>
int binarySearch(T arr[], int n, T target){

    int l = 0, r = n; // target在[l...r)的范围里
    while(l < r){    // 当 l == r 时, 区间[l...r)是一个无效区间
        int mid = l + (r - l) / 2;
        if(arr[mid] == target) return mid;
        if(target > arr[mid])
            l = mid + 1;    // target在[mid+1...r)中; [l...mid]一定没有target
        else// target < arr[mid]
            r = mid;        // target在[l...mid)中; [mid...r)一定没有target
    }

    return -1;
}
```
