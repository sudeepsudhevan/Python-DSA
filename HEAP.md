## MaxHeap

### 1. Constructor and Helper Methods
```py
class MaxHeap:
    def __init__(self):
        self.heap = []
    
    def _left_child(self, index):
        return 2 * index + 1
    
    def _right_child(self, index):
        return 2 * index + 2
        
    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1],self.heap[index2] = self.heap[index2],self.heap[index1] 
```
### 2. Insert
```py
class MaxHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]

    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1
        
        while current > 0 and self.heap[current] > self.heap[self._parent(current)]:
            self._swap(current,self._parent(current))
            current = self._parent(current)
    
    
    
myheap = MaxHeap()
myheap.insert(99)
myheap.insert(72)
myheap.insert(61)
myheap.insert(58)

print(myheap.heap)  


myheap.insert(100)

print(myheap.heap)  


myheap.insert(75)

print(myheap.heap)


"""
    EXPECTED OUTPUT:
    ----------------
    [99, 72, 61, 58]
    [100, 99, 61, 58, 72]
    [100, 99, 75, 58, 72, 61]

"""
    
```

### 3. Remove
```py
class MaxHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]

    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1

        while current > 0 and self.heap[current] > self.heap[self._parent(current)]:
            self._swap(current, self._parent(current))
            current = self._parent(current)
    
    def _sink_down(self, index):
        max_index = index
        while True:
            left_index = self._left_child(index)
            right_index = self._right_child(index)

            if (left_index < len(self.heap) and self.heap[left_index] > self.heap[max_index]):
                max_index = left_index

            if (right_index < len(self.heap) and self.heap[right_index] > self.heap[max_index]):
                max_index = right_index

            if max_index != index:
                self._swap(index, max_index)
                index = max_index
            else:
                return
                       
    def remove(self):
        if len(self.heap) == 0:
            return None
        
        if len(self.heap) == 1:
            return self.heap.pop()
        
        max_value = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._sink_down(0)
        
        return max_value    
        
    
    
    
myheap = MaxHeap()
myheap.insert(95)
myheap.insert(75)
myheap.insert(80)
myheap.insert(55)
myheap.insert(60)
myheap.insert(50)
myheap.insert(65)

print(myheap.heap)


myheap.remove()

print(myheap.heap)


myheap.remove()

print(myheap.heap)


"""
    EXPECTED OUTPUT:
    ----------------
    [95, 75, 80, 55, 60, 50, 65]
    [80, 75, 65, 55, 60, 50]
    [75, 60, 65, 55, 50]

"""
    
```
### 4. Sink down method
```py
class MaxHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]

    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1

        while current > 0 and self.heap[current] > self.heap[self._parent(current)]:
            self._swap(current, self._parent(current))
            current = self._parent(current)

    def _sink_down(self, index):
        max_index = index
        while True:
            left_index = self._left_child(index)
            right_index = self._right_child(index)
 
            if (left_index < len(self.heap) and 
                    self.heap[left_index] > self.heap[max_index]):
                max_index = left_index
 
            if (right_index < len(self.heap) and 
                    self.heap[right_index] > self.heap[max_index]):
                max_index = right_index
 
            if max_index != index:
                self._swap(index, max_index)
                index = max_index
            else:
                return
            
                       
    def remove(self):
        if len(self.heap) == 0:
            return None

        if len(self.heap) == 1:
            return self.heap.pop()

        max_value = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._sink_down(0)

        return max_value
        
        

myheap = MaxHeap()
myheap.insert(95)
myheap.insert(75)
myheap.insert(80)
myheap.insert(55)
myheap.insert(60)
myheap.insert(50)
myheap.insert(65)

print(myheap.heap)


myheap.remove()

print(myheap.heap)


myheap.remove()

print(myheap.heap)


"""
    EXPECTED OUTPUT:
    ----------------
    [95, 75, 80, 55, 60, 50, 65]
    [80, 75, 65, 55, 60, 50]
    [75, 60, 65, 55, 50]

"""

```
## MinHeap
### 1. Constructor and helper Method
```py
class MinHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]
```

### 2. Insert
```py
class MinHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]

    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1
        
        while current > 0 and self.heap[current] < self.heap[self._parent(current)]:
            self._swap(current, self._parent(current))
            current = self._parent(current)
 
 
myheap = MinHeap()
myheap.insert(12)
myheap.insert(10)
myheap.insert(8)
myheap.insert(6)

print(myheap.heap)  # [6, 8, 10, 12]

myheap.insert(4)

print(myheap.heap)  # [4, 6, 10, 12, 8]

myheap.insert(2)

print(myheap.heap)  # [2, 6, 4, 12, 8, 10]


"""
    EXPECTED OUTPUT:
    ----------------
    [6, 8, 10, 12]
    [4, 6, 10, 12, 8]
    [2, 6, 4, 12, 8, 10]

"""

```
### 3. Remove
```py
class MinHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]

    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1

        while current > 0 and self.heap[current] < self.heap[self._parent(current)]:
            self._swap(current, self._parent(current))
            current = self._parent(current)

    # We will be writing the _sink_down method in the next exercise.
    # But I need to include it here for the tests to work for remove.
    # So, don't peek at this one here.  :-)
    def _sink_down(self, index):
        min_index = index
        while True:
            left_index = self._left_child(index)
            right_index = self._right_child(index)

            if (left_index < len(self.heap) and 
                    self.heap[left_index] < self.heap[min_index]):
                min_index = left_index

            if (right_index < len(self.heap) and 
                    self.heap[right_index] < self.heap[min_index]):
                min_index = right_index

            if min_index != index:
                self._swap(index, min_index)
                index = min_index
            else:
                return

    def remove(self):
        if len(self.heap) == 0:
            return None
        
        if len(self.heap) == 1:
            return self.heap.pop()
        
        max_value = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._sink_down(0)
        
        return max_value 



myheap = MinHeap()
myheap.insert(12)
myheap.insert(10)
myheap.insert(8)
myheap.insert(6)
myheap.insert(4)
myheap.insert(2)

print(myheap.heap)  # [2, 6, 4, 12, 8, 10]

removed = myheap.remove()
print(f'Removed: {removed}, Heap: {myheap.heap}')  # Removed: 2, Heap: [4, 6, 10, 12, 8]

removed = myheap.remove()
print(f'Removed: {removed}, Heap: {myheap.heap}')  # Removed: 4, Heap: [6, 8, 10, 12]

removed = myheap.remove()
print(f'Removed: {removed}, Heap: {myheap.heap}')  # Removed: 6, Heap: [8, 12, 10]



"""
    EXPECTED OUTPUT:
    ----------------
    [2, 6, 4, 12, 8, 10]
    Removed: 2, Heap: [4, 6, 10, 12, 8]
    Removed: 4, Heap: [6, 8, 10, 12]
    Removed: 6, Heap: [8, 12, 10]

"""
```
### 4. Sink Down
```py
class MinHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]

    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1

        while current > 0 and self.heap[current] < self.heap[self._parent(current)]:
            self._swap(current, self._parent(current))
            current = self._parent(current)

    def _sink_down(self, index):
        min_index = index
        while True:
            left_index = self._left_child(index)
            right_index = self._right_child(index)

            if (left_index < len(self.heap) and 
                    self.heap[left_index] < self.heap[min_index]):
                min_index = left_index

            if (right_index < len(self.heap) and 
                    self.heap[right_index] < self.heap[min_index]):
                min_index = right_index

            if min_index != index:
                self._swap(index, min_index)
                index = min_index
            else:
                return
    

    def remove(self):
        if len(self.heap) == 0:
            return None

        if len(self.heap) == 1:
            return self.heap.pop()

        min_value = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._sink_down(0)

        return min_value
        
        
        
myheap = MinHeap()
myheap.insert(12)
myheap.insert(10)
myheap.insert(8)
myheap.insert(6)
myheap.insert(4)
myheap.insert(2)

print(myheap.heap)  # [2, 6, 4, 12, 8, 10]

removed = myheap.remove()
print(f'Removed: {removed}, Heap: {myheap.heap}')  # Removed: 2, Heap: [4, 6, 10, 12, 8]

removed = myheap.remove()
print(f'Removed: {removed}, Heap: {myheap.heap}')  # Removed: 4, Heap: [6, 8, 10, 12]

removed = myheap.remove()
print(f'Removed: {removed}, Heap: {myheap.heap}')  # Removed: 6, Heap: [8, 12, 10]



"""
    EXPECTED OUTPUT:
    ----------------
    [2, 6, 4, 12, 8, 10]
    Removed: 2, Heap: [4, 6, 10, 12, 8]
    Removed: 4, Heap: [6, 8, 10, 12]
    Removed: 6, Heap: [8, 12, 10]

"""
```
## More Problems
### 1. Heap: Kth Smallest Element in an Array
```py
class MaxHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]

    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1

        while current > 0 and self.heap[current] > self.heap[self._parent(current)]:
            self._swap(current, self._parent(current))
            current = self._parent(current)

    def _sink_down(self, index):
        max_index = index
        while True:
            left_index = self._left_child(index)
            right_index = self._right_child(index)

            if (left_index < len(self.heap) and 
                    self.heap[left_index] > self.heap[max_index]):
                max_index = left_index

            if (right_index < len(self.heap) and 
                    self.heap[right_index] > self.heap[max_index]):
                max_index = right_index

            if max_index != index:
                self._swap(index, max_index)
                index = max_index
            else:
                return
                       
    def remove(self):
        if len(self.heap) == 0:
            return None

        if len(self.heap) == 1:
            return self.heap.pop()

        max_value = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._sink_down(0)

        return max_value




def find_kth_smallest(nums, k):
    max_heap = MaxHeap()
 
    for num in nums:
        max_heap.insert(num)
        if len(max_heap.heap) > k:
            max_heap.remove()
 
    return max_heap.remove()




# Test cases
nums = [[3,2,1,5,6,4], [6,5,4,3,2,1], [1,2,3,4,5,6], [3,2,3,1,2,4,5,5,6]]
ks = [2, 3, 4, 7]
expected_outputs = [2, 3, 4, 5]

for i in range(len(nums)):
    print(f'Test case {i+1}...')
    print(f'Input: {nums[i]} with k = {ks[i]}')
    result = find_kth_smallest(nums[i], ks[i])
    print(f'Output: {result}')
    print(f'Expected output: {expected_outputs[i]}')
    print(f'Test passed: {result == expected_outputs[i]}')
    print('---------------------------------------')


"""
    EXPECTED OUTPUT:
    ----------------
    Test case 1...
    Input: [3, 2, 1, 5, 6, 4] with k = 2
    Output: 2
    Expected output: 2
    Test passed: True
    ---------------------------------------
    Test case 2...
    Input: [6, 5, 4, 3, 2, 1] with k = 3
    Output: 3
    Expected output: 3
    Test passed: True
    ---------------------------------------
    Test case 3...
    Input: [1, 2, 3, 4, 5, 6] with k = 4
    Output: 4
    Expected output: 4
    Test passed: True
    ---------------------------------------
    Test case 4...
    Input: [3, 2, 3, 1, 2, 4, 5, 5, 6] with k = 7
    Output: 5
    Expected output: 5
    Test passed: True
    ---------------------------------------

"""


```
### 2. Heap: Maximum Element in a Stream
```py
class MaxHeap:
    def __init__(self):
        self.heap = []

    def _left_child(self, index):
        return 2 * index + 1

    def _right_child(self, index):
        return 2 * index + 2

    def _parent(self, index):
        return (index - 1) // 2

    def _swap(self, index1, index2):
        self.heap[index1], self.heap[index2] = self.heap[index2], self.heap[index1]

    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1

        while current > 0 and self.heap[current] > self.heap[self._parent(current)]:
            self._swap(current, self._parent(current))
            current = self._parent(current)

    def _sink_down(self, index):
        max_index = index
        while True:
            left_index = self._left_child(index)
            right_index = self._right_child(index)

            if (left_index < len(self.heap) and 
                    self.heap[left_index] > self.heap[max_index]):
                max_index = left_index

            if (right_index < len(self.heap) and 
                    self.heap[right_index] > self.heap[max_index]):
                max_index = right_index

            if max_index != index:
                self._swap(index, max_index)
                index = max_index
            else:
                return
                       
    def remove(self):
        if len(self.heap) == 0:
            return None

        if len(self.heap) == 1:
            return self.heap.pop()

        max_value = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._sink_down(0)

        return max_value
        


def stream_max(nums):
    max_heap = MaxHeap()
    max_stream = []
 
    for num in nums:
        max_heap.insert(num)
        max_stream.append(max_heap.heap[0])
 
    return max_stream



test_cases = [
    ([], []),
    ([1], [1]),
    ([1, 2, 3, 4, 5], [1, 2, 3, 4, 5]),
    ([1, 2, 2, 1, 3, 3, 3, 2, 2], [1, 2, 2, 2, 3, 3, 3, 3, 3]),
    ([-1, -2, -3, -4, -5], [-1, -1, -1, -1, -1])
]

for i, (nums, expected) in enumerate(test_cases):
    result = stream_max(nums)
    print(f'\nTest {i+1}')
    print(f'Input: {nums}')
    print(f'Expected Output: {expected}')
    print(f'Actual Output: {result}')
    if result == expected:
        print('Status: Passed')
    else:
        print('Status: Failed')



"""
    EXPECTED OUTPUT:
    ----------------
    Test 1
    Input: []
    Expected Output: []
    Actual Output: []
    Status: Passed
    Test 2
    Input: [1]
    Expected Output: [1]
    Actual Output: [1]
    Status: Passed
    Test 3
    Input: [1, 2, 3, 4, 5]
    Expected Output: [1, 2, 3, 4, 5]
    Actual Output: [1, 2, 3, 4, 5]
    Status: Passed
    Test 4
    Input: [1, 2, 2, 1, 3, 3, 3, 2, 2]
    Expected Output: [1, 2, 2, 2, 3, 3, 3, 3, 3]
    Actual Output: [1, 2, 2, 2, 3, 3, 3, 3, 3]
    Status: Passed
    Test 5
    Input: [-1, -2, -3, -4, -5]
    Expected Output: [-1, -1, -1, -1, -1]
    Actual Output: [-1, -1, -1, -1, -1]
    Status: Passed

"""


```
