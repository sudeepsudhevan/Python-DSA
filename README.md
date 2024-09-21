# Python-DSA

## Linked List

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
    def __init__(self, value=None):
        new_node = Node(value)
        self.head = new_node
        self.tail = new_node
        self.length = 1

my_linked_list = LinkedList(4)
```
