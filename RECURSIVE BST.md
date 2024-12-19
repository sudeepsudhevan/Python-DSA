## Recursive Binary Search Tree
### 1. contains
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
        

class BinarySearchTree:
    def __init__(self):
        self.root = None

    def insert(self, value):
        new_node = Node(value)
        if self.root is None:
            self.root = new_node
            return True
        temp = self.root
        while (True):
            if new_node.value == temp.value:
                return False
            if new_node.value < temp.value:
                if temp.left is None:
                    temp.left = new_node
                    return True
                temp = temp.left
            else: 
                if temp.right is None:
                    temp.right = new_node
                    return True
                temp = temp.right
        
    def __r_contains(self, current_node, value):
        if current_node == None:
            return False
        
        if value == current_node.value:
            return True
        
        if value < current_node.value:
            return self.__r_contains(current_node.left,value)
        
        if value > current_node.value:
            return self.__r_contains(current_node.right,value)
            
    def r_contains(self,value):
        return self.__r_contains(self.root,value)
        


my_tree = BinarySearchTree()
my_tree.insert(47)
my_tree.insert(21)
my_tree.insert(76)
my_tree.insert(18)
my_tree.insert(27)
my_tree.insert(52)
my_tree.insert(82)

print('BST Contains 27:')
print(my_tree.r_contains(27))

print('\nBST Contains 17:')
print(my_tree.r_contains(17))
                


"""
    EXPECTED OUTPUT:
    ----------------
    BST Contains 27:
    True

    BST Contains 17:
    False

"""
```
### 2. Insert
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
        

class BinarySearchTree:
    def __init__(self):
        self.root = None

    def __r_insert(self,current_node,value):
        if current_node ==  None:
            return Node(value)
        
        if value < current_node.value:
            current_node.left = self.__r_insert(current_node.left, value)
        
        if value > current_node.value:
            current_node.right = self.__r_insert(current_node.right, value)
        
        return current_node

    def r_insert(self, value):
        if self.root == None: 
            self.root = Node(value)
        self.__r_insert(self.root, value)  

##########################################################   
##   Test code below will print output to "User logs"   ##
##########################################################

def check(expect, actual, message):
    print(message)
    print("EXPECTED:", expect)
    print("RETURNED:", actual)
    print("PASS" if expect == actual else "FAIL", "\n")

print("\n----- Test: Insert into an empty tree -----\n")
bst = BinarySearchTree()
print("Inserting value:", 5)
bst.r_insert(5)
check(5, bst.root.value, "Root value after inserting 5:")
check(None, bst.root.left, "Left child of root:")
check(None, bst.root.right, "Right child of root:")

print("\n----- Test: Insert values in ascending order -----\n")
bst = BinarySearchTree()
values = [1, 2, 3, 4, 5]
for val in values:
    print("Inserting value:", val)
    bst.r_insert(val)

# Check tree structure
check(1, bst.root.value, "Root value:")
check(2, bst.root.right.value, "Right child of root:")
check(3, bst.root.right.right.value, "Right child of right child of root:")
check(4, bst.root.right.right.right.value, "Right child's right child's right child of root:")
check(5, bst.root.right.right.right.right.value, "Fourth right child of root:")

print("\n----- Test: Insert values in descending order -----\n")
bst = BinarySearchTree()
values = [5, 4, 3, 2, 1]
for val in values:
    print("Inserting value:", val)
    bst.r_insert(val)

# Check tree structure
check(5, bst.root.value, "Root value:")
check(4, bst.root.left.value, "Left child of root:")
check(3, bst.root.left.left.value, "Left child of left child of root:")
check(2, bst.root.left.left.left.value, "Left child's left child's left child of root:")
check(1, bst.root.left.left.left.left.value, "Fourth left child of root:")

print("\n----- Test: Insert values in mixed order -----\n")
bst = BinarySearchTree()
values = [3, 1, 4, 5, 2]
for val in values:
    print("Inserting value:", val)
    bst.r_insert(val)

# Check tree structure
check(3, bst.root.value, "Root value:")
check(1, bst.root.left.value, "Left child of root:")
check(2, bst.root.left.right.value, "Right child of left child of root:")
check(4, bst.root.right.value, "Right child of root:")
check(5, bst.root.right.right.value, "Right child of right child of root:")

print("\n----- Test: Insert duplicate values -----\n")
bst = BinarySearchTree()
values = [3, 3, 3]
for val in values:
    print("Inserting value:", val)
    bst.r_insert(val)

# Check tree structure
check(3, bst.root.value, "Root value:")
check(None, bst.root.left, "Left child of root:")
check(None, bst.root.right, "Right child of root:")

```
### 3. Min Value
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
        

class BinarySearchTree:
    def __init__(self):
        self.root = None

    def insert(self, value):
        new_node = Node(value)
        if self.root is None:
            self.root = new_node
            return True
        temp = self.root
        while (True):
            if new_node.value == temp.value:
                return False
            if new_node.value < temp.value:
                if temp.left is None:
                    temp.left = new_node
                    return True
                temp = temp.left
            else: 
                if temp.right is None:
                    temp.right = new_node
                    return True
                temp = temp.right
    
    def min_value(self, current_node):
        while current_node.left is not None:
            current_node = current_node.left
        return current_node.value
        
        

my_tree = BinarySearchTree()
my_tree.insert(47)
my_tree.insert(21)
my_tree.insert(76)
my_tree.insert(18)
my_tree.insert(27)
my_tree.insert(52)
my_tree.insert(82)


print( my_tree.min_value(my_tree.root) )

print( my_tree.min_value(my_tree.root.right) )
            

"""
    EXPECTED OUTPUT:
    ----------------
	18
	52

"""
```
### 4. Delete
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
        

class BinarySearchTree:
    def __init__(self):
        self.root = None

          
    def __r_insert(self, current_node, value):
        if current_node == None: 
            return Node(value)   
        if value < current_node.value:
            current_node.left = self.__r_insert(current_node.left, value)
        if value > current_node.value:
            current_node.right = self.__r_insert(current_node.right, value) 
        return current_node    

    def r_insert(self, value):
        if self.root == None: 
            self.root = Node(value)
        self.__r_insert(self.root, value)  


    def min_value(self, current_node):
        while (current_node.left is not None):
            current_node = current_node.left
        return current_node.value 

    def __delete_node(self, current_node, value):
	    if current_node == None: 
		    return None
	    if value < current_node.value:
		    current_node.left = self.__delete_node(current_node.left, value)
	    elif value > current_node.value: 
		    current_node.right = self.__delete_node(current_node.right, value)
	    else:									### code where we find the node
		    if current_node.left == None and current_node.right == None:
			    return None
		    elif current_node.left == None:
			    current_node = current_node.right
		    elif current_node.right == None:
			    current_node = current_node.left
		    else:
			    sub_tree_min = self.min_value(current_node.right)
			    current_node.value = sub_tree_min
			    current_node.right = self.__delete_node(current_node.right, sub_tree_min)
	    return current_node

        

    def delete_node(self, value):
        return self.__delete_node(self.root, value)

##########################################################   
##   Test code below will print output to "User logs"   ##
##########################################################

def check(expect, actual, message):
    print(message)
    print("EXPECTED:", expect)
    print("RETURNED:", actual)
    print("PASS" if expect == actual else "FAIL", "\n")


# test_delete_node_no_children
print("\n----- Test: Delete node with no children -----\n")
bst = BinarySearchTree()
values = [5, 3, 8]
for v in values:
    print("Inserting value:", v)
    bst.r_insert(v)
bst.delete_node(3)
check(None, bst.root.left, "Left child of root after deleting 3:")


# test_delete_node_only_left_child
print("\n----- Test: Delete node with only left child -----\n")
bst = BinarySearchTree()
values = [5, 3, 8, 1]
for v in values:
    print("Inserting value:", v)
    bst.r_insert(v)
bst.delete_node(3)
check(1, bst.root.left.value, "Left child of root after deleting 3:")


# test_delete_node_only_right_child
print("\n----- Test: Delete node with only right child -----\n")
bst = BinarySearchTree()
values = [5, 3, 8, 9]
for v in values:
    print("Inserting value:", v)
    bst.r_insert(v)
bst.delete_node(8)
check(9, bst.root.right.value, "Right child of root after deleting 8:")


# test_delete_node_two_children
print("\n----- Test: Delete node with two children -----\n")
bst = BinarySearchTree()
values = [5, 3, 8, 1, 4, 7, 9]
for v in values:
    print("Inserting value:", v)
    bst.r_insert(v)
bst.delete_node(3)
check(4, bst.root.left.value, "Left child of root after deleting 3:")


# test_delete_root
print("\n----- Test: Delete root -----\n")
bst = BinarySearchTree()
values = [5, 3, 8]
for v in values:
    print("Inserting value:", v)
    bst.r_insert(v)
bst.delete_node(5)
check(8, bst.root.value, "Root value after deleting 5:")


# test_delete_non_existent_node
print("\n----- Test: Attempt to delete a non-existent node -----\n")
bst = BinarySearchTree()
values = [5, 3, 8]
for v in values:
    print("Inserting value:", v)
    bst.r_insert(v)
original_root_value = bst.root.value
bst.delete_node(10)
check(original_root_value, bst.root.value, "Root value after attempting to delete 10:")

```
