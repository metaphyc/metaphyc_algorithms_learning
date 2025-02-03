# 排序
## 插入排序
从第2个元素开始向右将每个元素插入到其左边数组中正确的位置，通过从头向右寻找第一个大于其的元素找到正确的位置
```python
def insertsort(array):
    for i in range(1, len(array)):
        for j in range(i):
            if array[j] > array[i]:
                a = array.pop(i)
                array.insert(j, a)
```

## 选择排序
## 归并排序
## 冒泡排序

# 查找
## 线性查找
## 二分查找

# 霍纳规则
