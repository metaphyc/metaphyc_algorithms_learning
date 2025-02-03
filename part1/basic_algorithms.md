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
- 分解    将数组分解为两个各包含一半元素的子数组
- 解决    使用归并排序递归地排序两个子数组
- 合并    合并两个已排序的子数组以产生已排序的答案
```python
def mergeSort(arr):
    if len(arr) < 2:
        return arr
    else:
        mid = len(arr) / 2
        return merge(mergeSort(arr[0: mid], mergeSort(arr[(mid + 1):])

def merge(arr1, arr2):
    result = []
    while arr1 and arr2:
        if arr1[0] < arr2[0]:
            result.append(arr1.pop())
        else:
            result.append(arr2.pop())
    whlie arr1:
        result.append(arr1.pop())
    while arr2:
        result.append(arr1.pop())
    return result
```

## 冒泡排序

# 查找
## 线性查找
## 二分查找

# 霍纳规则
