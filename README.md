# Python-DSA

## Linked List

### 1. Constructor

To create a new Node
```py
class Node:
    """
    Class that implements the Node of a linked list.

    Attributes:
        value: value of the node.
        next: pointer to the next node.
    """
    def __init__(self, value):
        self.value = value
        self.next = None
```

Create a Linked List
```py
class LinkedList:
    """
    This class is an implementation of a linked list data structure.
    """
    def __init__(self, value):
        new_node = Node(value)
        self.head = new_node
        self.tail = new_node
        self.length = 1

my_linked_list = LinkedList(4)

print('Head:', my_linked_list.head.value) # Head: 4
print('Tail:', my_linked_list.tail.value) # Tail: 4
print('Length:', my_linked_list.length)   # Length: 1
```

Print The values in linked list
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        

class LinkedList:
    def __init__(self, value):
        new_node = Node(value)
        self.head = new_node
        self.tail = new_node
        self.length = 1

    # used function
    def print_list(self):
        temp = self.head
        while temp is not None:
            print(temp.value)
            temp = temp.next
    
    def make_empty(self):
        self.head = None
        self.tail = None
        self.length = 0
        
    def append(self, value):
        new_node = Node(value)
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
        self.length += 1



my_linked_list = LinkedList(1)
my_linked_list.append(2)
my_linked_list.append(3)

my_linked_list.print_list()


"""
    EXPECTED OUTPUT:
    ----------------
    1
    2
    3
    
"""

```
