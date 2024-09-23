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
### 2. Append
Append an item to linked list

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
            self.tail.next = new_node # in practical Here adding the new node to tail node next ie.(nodelast.next = new_node)
            self.tail = new_node      # here setting the new node as new tail node ie.(nodelast = new_node)
        
        self.length += 1




my_linked_list = LinkedList(1)
my_linked_list.make_empty()

my_linked_list.append(1)
my_linked_list.append(2)

print('Head:', my_linked_list.head.value)
print('Tail:', my_linked_list.tail.value)
print('Length:', my_linked_list.length, '\n')

print('Linked List:')
my_linked_list.print_list()



"""
    EXPECTED OUTPUT:
    ----------------
    Head: 1
    Tail: 2
    Length: 2 

    Linked List:
    1
    2
    
"""

```
### 3. Pop
Pop an Item from the Linked List
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

    def print_list(self):
        values = []
        temp = self.head
        while temp is not None:
            values.append(str(temp.value))
            temp = temp.next
        values.append("None")
        print(" -> ".join(values))
        
    def append(self, value):
        new_node = Node(value)
        if self.length == 0:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
        self.length += 1
        return True

    def pop(self):
        if self.length == 0:
            return None
        
        pre = self.head
        temp = self.head
        while temp.next is not None:
            pre = temp
            temp = temp.next
        
        self.tail = pre
        self.tail.next = None
        self.length -= 1
        
        if self.length == 0:
            self.head = None
            self.tail = None
        return temp
        
        
 
##########################################################   
##   Test code below will print output to "User logs"   ##
##########################################################

def check(expect, actual, message):
    print(message)
    print("EXPECTED:", expect)
    print("RETURNED:", actual)
    print("PASS" if expect == actual else "FAIL", "\n")

print("\n----- Test: Pop on linked list with one node -----\n")
linked_list = LinkedList(1)
linked_list.print_list()
popped_node = linked_list.pop()
check(1, popped_node.value, "Value of popped node:")
check(None, linked_list.head, "Head of linked list:")
check(None, linked_list.tail, "Tail of linked list:")
check(0, linked_list.length, "Length of linked list:")

print("\n----- Test: Pop on linked list with multiple nodes -----\n")
linked_list = LinkedList(1)
linked_list.append(2)
linked_list.append(3)
linked_list.print_list()
popped_node = linked_list.pop()
check(3, popped_node.value, "Value of popped node:")
check(1, linked_list.head.value, "Head of linked list:")
check(2, linked_list.tail.value, "Tail of linked list:")
check(2, linked_list.length, "Length of linked list:")

print("\n----- Test: Pop on empty linked list -----\n")
linked_list = LinkedList(1)
linked_list.head = None
linked_list.tail = None
linked_list.length = 0
popped_node = linked_list.pop()
check(None, popped_node, "Popped node from empty linked list:")
check(None, linked_list.head, "Head of linked list:")
check(None, linked_list.tail, "Tail of linked list:")
check(0, linked_list.length, "Length of linked list:")

print("\n----- Test: Pop all -----\n")
linked_list = LinkedList(1)
linked_list.append(2)
linked_list.print_list()
popped_node = linked_list.pop()
check(2, popped_node.value, "Value of popped node (first pop):")
check(1, linked_list.head.value, "Head of linked list (after first pop):")
check(1, linked_list.tail.value, "Tail of linked list (after first pop):")
check(1, linked_list.length, "Length of linked list (after first pop):")
popped_node = linked_list.pop()
check(1, popped_node.value, "Value of popped node (second pop):")
check(None, linked_list.head, "Head of linked list (after second pop):")
check(None, linked_list.tail, "Tail of linked list (after second pop):")
check(0, linked_list.length, "Length of linked list (after second pop):")
popped_node = linked_list.pop()
check(None, popped_node, "Popped node from empty linked list (third pop):")
check(None, linked_list.head, "Head of linked list (after third pop):")
check(None, linked_list.tail, "Tail of linked list (after third pop):")
check(0, linked_list.length, "Length of linked list (after third pop):")

```
### 4. Prepend
Prepend an Item to the Linked List
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

    def print_list(self):
        temp = self.head
        while temp is not None:
            print(temp.value)
            temp = temp.next
        
    def append(self, value):
        new_node = Node(value)
        if self.length == 0:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
        self.length += 1
        return True

    def pop(self):
        if self.length == 0:
            return None
        temp = self.head
        pre = self.head
        while(temp.next):
            pre = temp
            temp = temp.next
        self.tail = pre
        self.tail.next = None
        self.length -= 1
        if self.length == 0:
            self.head = None
            self.tail = None
        return temp

    def prepend(self,value):
        new_node = Node(value)
        if self.length == 0:
            self.head = new_node
            self.tail = new_node
        else:
            new_node.next = self.head
            self.head = new_node
        self.length +=1


my_linked_list = LinkedList(2)
my_linked_list.append(3)

print('Before prepend():')
print('----------------')
print('Head:', my_linked_list.head.value)
print('Tail:', my_linked_list.tail.value)
print('Length:', my_linked_list.length, '\n')
print('Linked List:')
my_linked_list.print_list()


my_linked_list.prepend(1)


print('\n\nAfter prepend():')
print('---------------')
print('Head:', my_linked_list.head.value)
print('Tail:', my_linked_list.tail.value)
print('Length:', my_linked_list.length, '\n')
print('Linked List:')
my_linked_list.print_list()



"""
    EXPECTED OUTPUT:
    
    Before prepend():
    ----------------
    Head: 2
    Tail: 3
    Length: 2 

    Linked List:
    2
    3


    After prepend():
    ---------------
    Head: 1
    Tail: 3
    Length: 3 

    Linked List:
    1
    2
    3   

"""
```
