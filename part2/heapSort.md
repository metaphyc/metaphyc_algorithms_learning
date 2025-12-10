# 堆排序
## 堆
**（二叉）堆** 是一个数组，它可以被看成一个完全二叉树。
树上的每一个结点对应数组中的一个元素。
除了最底层外，该树是完全充满的，而且是从左向右填充。

## 维护堆的性质
maxHeapify是用于维护最大堆性质的重要过程。
```python
def maxHeapify(arr, idx, heapSize):
    left = 2 * idx + 1
    right = 2 * idx + 2
    largest = idx
    if left < heapSize and arr[left] > arr[largest]:
        largest = left
    if right < heapSize and arr[right] > arr[largest]:
        largest = right
    if largest != idx:
        arr[idx], arr[largest] = arr[largest], arr[idx]
        maxHeapify(arr, largest, heapSize)
```

## 建堆
我们可以用自底向上的方法利用maxHeapify把一个大小为 $n$ 的数组转换为最大堆。
```python
def buildMaxHeap(arr):
    heapSize = len(arr)
    for i in range(heapSize // 2, -1, -1):
        maxHeapify(arr, i, heapSize)
```

## 堆排序算法
初始时候，堆排序算法利用buildMaxHeap将输入数组建成最大堆。
在每次循环中
- 因为数组中的最大元素总在根结点arr[0]中，通过把它与arr[i]进行互换，我们可以让该元素放到正确的位置。
- 这时候，我们从堆中去掉结点i(这一操作可以通过减少heapSize的值来实现），剩余的结点中，原来根的孩子结点仍然是最大堆，而新的根结点可能会违背最大堆的性质。
- 为了维护最大堆的性质，我们要做的是调用maxHeapify(arr, 0, heapSize), 从而构造一个新的最大堆。

堆排序算法会不断重复这一过程，直到堆的大小从 $n$ 降到2。
```python
def heapSort(arr):
    buildMaxHeap(arr)
    heapSize = len(arr)
    for i in range(len(arr) - 1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]
        heapSize -= 1
        maxHeapify(arr, 0, heapSize)
```

## 基于最大堆实现最大优先队列
### maximum
heapMaximum可以在 $\Theta(1)$ 时间内实现maximum操作。
```python
def heapMaximum(arr):
    return arr[0]
```

### extractMax
heapExtractMax可以在 $\Theta(\lg n)$ 时间内实现extractMax操作。
- 交换根节点和末节点
- 弹出最大值（末节点）
- 维护最大堆性质
```python
def heapExtractMax(arr):
    if len(arr) < 1:
        return 'heap underflow'
    maxElem = arr[0]
    arr[0] = arr[-1]
    arr.pop()
    maxHeapify(arr, 0, len(arr))
    return maxElem
```

### increaseKey
heapIncreaseKey可以在 $\Theta(\lg n)$ 时间内实现increaseKey操作。
- 更新key值
- 不断与父节点交换直到值小于父节点
```python
def heapIncreaseKey(arr, idx, key):
    if key < arr[idx]:
        return 'new key is smaller than current key'
    arr[idx] = key
    while idx > 0 and arr[(idx - 1) // 2] < arr[idx]:
        arr[idx], arr[(idx - 1) // 2] = arr[(idx - 1) // 2], arr[idx]
        idx = (idx - 1) // 2
```

### insert
maxHeapInsert可以在 $\Theta(\lg n)$ 时间内实现insert操作。
- 增加值为 $- \infty$ 的叶节点
- 调用heapIncreaseKey将其更新为key
```python
def heapInsert(arr, key):
    arr.append(float('-inf'))
    heapIncreaseKey(arr, len(arr) - 1, key)
```

