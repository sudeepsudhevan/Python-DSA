## STACK
### 1. Constructor
```py
class Node:
    def __init__(self,value):
        self.value = value
        self.next = None
        
class Stack:
    def __init__(self,value):
        new_node = Node(value)
        self.top = new_node
        self.height = 1
    


my_stack = Stack(4)

print('Top:', my_stack.top.value)
print('Height:', my_stack.height)



"""
    EXPECTED OUTPUT:
    ----------------
    Top: 4
    Height: 1

"""
```
### 2. Stack Push
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        

class Stack:
    def __init__(self, value):
        new_node = Node(value)
        self.top = new_node
        self.height = 1

    def print_stack(self):
        temp = self.top
        while temp is not None:
            print(temp.value)
            temp = temp.next

    def push(self,value):
        new_node = Node(value)
        
        if self.height == 0:
            self.top = new_node
        else:
            new_node.next = self.top
            self.top = new_node
        
        self.height += 1
        

my_stack = Stack(2)

print('Stack before push(1):')
my_stack.print_stack()

my_stack.push(1)

print('\nStack after push(1):')
my_stack.print_stack()



"""
    EXPECTED OUTPUT:
    ----------------
    Stack before push(1):
    2

    Stack after push(1):
    1
    2   

"""

```
### 3. Stack Pop
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        

class Stack:
    def __init__(self, value):
        new_node = Node(value)
        self.top = new_node
        self.height = 1

    def print_stack(self):
        temp = self.top
        while temp is not None:
            print(temp.value)
            temp = temp.next

    def push(self, value):
        new_node = Node(value)
        if self.height == 0:
            self.top = new_node
        else:
            new_node.next = self.top
            self.top = new_node
        self.height += 1
        return True

    def pop(self):
        if self.height == 0:
            return None
    
        temp = self.top
        self.top = self.top.next
        temp.next = None
        self.height -= 1
        return temp


my_stack = Stack(4)
my_stack.push(3)
my_stack.push(2)
my_stack.push(1)

print('Stack before pop():')
my_stack.print_stack()

print('\nPopped node:')
print(my_stack.pop().value)

print('\nStack after pop():')
my_stack.print_stack()



"""
    EXPECTED OUTPUT:
    ----------------
    Stack before pop():
    1
    2
    3
    4

    Popped node:
    1

    Stack after pop():
    2
    3
    4

"""
```

## Queue
### 1. Constructor
```py
class Node:
    def __init__(self,value):
        self.value = value
        self.next = None
    
        
class Queue:
    def __init__(self,value):
        new_node = Node(value)
        self.first = new_node
        self.last = new_node
        self.length = 1
    

my_queue = Queue(4)

print('First:', my_queue.first.value)
print('Last:', my_queue.last.value)
print('Length:', my_queue.length)


"""
    EXPECTED OUTPUT:
    ----------------
    First: 4
    Last: 4
    Length: 1

"""
```
### 2. Enqueue
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        

class Queue:
    def __init__(self, value):
        new_node = Node(value)
        self.first = new_node
        self.last = new_node
        self.length = 1

    def print_queue(self):
        temp = self.first
        while temp is not None:
            print(temp.value)
            temp = temp.next
        
    def enqueue(self,value):
        new_node = Node(value)
        
        if self.first is None:
            self.first = new_node
            self.last = new_node
        else:
            self.last.next = new_node
            self.last = new_node
        self.length += 1
        
my_queue = Queue(1)

print('Queue before enqueue(2):')
my_queue.print_queue()

my_queue.enqueue(2)

print('\nQueue after enqueue(2):')
my_queue.print_queue()



"""
    EXPECTED OUTPUT:
    ----------------
    Queue before enqueue(2):
    1

    Queue after enqueue(2):
    1
    2

"""
```
### 3. Dequeue
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        

class Queue:
    def __init__(self, value):
        new_node = Node(value)
        self.first = new_node
        self.last = new_node
        self.length = 1

    def print_queue(self):
        temp = self.first
        while temp is not None:
            print(temp.value)
            temp = temp.next
        
    def enqueue(self, value):
        new_node = Node(value)
        if self.first is None:
            self.first = new_node
            self.last = new_node
        else:
            self.last.next = new_node
            self.last = new_node
        self.length += 1
        return True

    def dequeue(self):
        if self.length == 0:
            return None
        
        temp = self.first
        if self.length == 1:
            self.first = None
            self.last = None
        else:
            self.first = self.first.next
            temp.next = None
        
        self.length -= 1
        return temp


my_queue = Queue(1)
my_queue.enqueue(2)

# (2) Items - Returns 2 Node
print(my_queue.dequeue().value)
# (1) Item -  Returns 1 Node
print(my_queue.dequeue().value)
# (0) Items - Returns None
print(my_queue.dequeue())



"""
    EXPECTED OUTPUT:
    ----------------
    1
    2
    None

"""
```
## Extra Questions
### 1. Stack: Implement Stack Using a List
```py
class Stack:
    def __init__(self):
        self.stack_list = []
```

### 2. Stack: Push for Stack That Uses List
```py
class Stack:
    def __init__(self):
        self.stack_list = []
        
    def print_stack(self):
        for i in range(len(self.stack_list)-1, -1, -1):
            print(self.stack_list[i])

    def push(self,value):
        self.stack_list.append(value)


my_stack = Stack()
my_stack.push(1)
my_stack.push(2)
my_stack.push(3)

my_stack.print_stack()



"""
    EXPECTED OUTPUT:
    ----------------
    3 
    2
    1
 
"""
```
### 3. Stack: Pop for Stack That Uses List 
```py
class Stack:
    def __init__(self):
        self.stack_list = []

    def print_stack(self):
        for i in range(len(self.stack_list)-1, -1, -1):
            print(self.stack_list[i])

    def is_empty(self):
        return len(self.stack_list) == 0

    def peek(self):
        if self.is_empty():
            return None
        else:
            return self.stack_list[-1]

    def size(self):
        return len(self.stack_list)

    def push(self, value):
        self.stack_list.append(value)

    def pop(self):
        if self.is_empty():
            return None
        else:    
            return self.stack_list.pop()
 
            
my_stack = Stack()
my_stack.push(1)
my_stack.push(2)
my_stack.push(3)

print("Stack before pop():")
my_stack.print_stack()

print("\nPopped node:")
print(my_stack.pop())

print("\nStack after pop():")
my_stack.print_stack()



"""
    EXPECTED OUTPUT:
    ----------------
    Stack before pop():
    3
    2
    1
    
    Popped node:
    3
    
    Stack after pop():
    2
    1
 
"""
```
