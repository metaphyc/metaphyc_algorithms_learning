# 排序
## 插入排序
从第2个元素开始向右将每个元素插入到其左边数组中正确的位置，通过从头向右寻找第一个大于其的元素找到正确的位置
```python
def insertSort(arr):
    for i in range(1, len(arr)):
        for j in range(i):
            if arr[j] > arr[i]:
                a = arr.pop(i)
                arr.insert(j, a)
```

## 选择排序
从第一个元素开始向右到倒数第二个元素，依次将其及右边中的最小值与其交换
```python
def selectionSort(arr):
    for i in range(len(arr) - 1):
        minIdx = i
        for j in range(i + 1, len(arr)):
            if arr[j] < arr[minIdx]:
                minIdx = j
            arr[minIdx], arr[i] = arr[i], arr[minIdx]
```

## 归并排序
分治算法
- **分解**    将数组分解为两个各包含一半元素的子数组
- **解决**    使用归并排序递归地排序两个子数组，若子数组只包含1个元素，则直接返回
- **合并**    合并两个已排序的子数组以产生已排序的答案
```python
def mergeSort(arr):
    if len(arr) < 2:
        return arr
    mid = len(arr) // 2
    return merge(mergeSort(arr[0: mid]), mergeSort(arr[mid:]))

def merge(arr1, arr2):
    result = []
    while arr1 and arr2:
        if arr1[0] < arr2[0]:
            result.append(arr1.pop(0))
        else:
            result.append(arr2.pop(0))
    while arr1:
        result.append(arr1.pop(0))
    while arr2:
        result.append(arr1.pop(0))
    return result
```

## 冒泡排序
重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来
```python
def bubbleSort(arr):
    for i in range(len(arr) - 1):
        for j in range(len(arr) - i  - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
```

> [!WARNING]
> - 插入排序、选择排序和冒泡排序均为原址排序，可直接在原数组上操作
> - 归并排序不是原址排序，需要用一个新数组保存排序结果

# 查找
## 线性查找
从左向右在列表中依次查找指定元素，返回其索引，未查到返回-1
```python
def linearSearch(list, x):
    for i in range(len(list)):
        if list[i] == x:
            return i
    return -1
```

## 二分查找
若列表为有序递增数组，可将指定元素与数组中点值比较，根据结果，只在其中一半的子数组中搜索
```python
def binarySearch(arr, x, left=0, right=None):
    if right == None:
        right = len(arr) - 1
    if left <= right: 
        mid = (left + right) // 2
        if arr[mid] == x:
            return mid
        elif arr[mid] < x:
            return binarySearch(arr, x, mid + 1, right)
        elif arr[mid] > x:
            return binarySearch(arr, x, left, mid - 1)
    return -1 
```

# 霍纳规则
