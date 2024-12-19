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
### 5. Convert Sorted List to Balanced BST
```py
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

class BinarySearchTree:
    def __init__(self):
        self.root = None
    
    # The 'is_balanced' and 'inorder_traversal' methods will 
    # be used to test your code
    def is_balanced(self, node=None):
        def check_balance(node):
            if node is None:
                return True, -1
            left_balanced, left_height = check_balance(node.left)
            if not left_balanced:
                return False, 0
            right_balanced, right_height = check_balance(node.right)
            if not right_balanced:
                return False, 0
            balanced = abs(left_height - right_height) <= 1
            height = 1 + max(left_height, right_height)
            return balanced, height

        balanced, _ = check_balance(self.root if node is None else node)
        return balanced
        
    def inorder_traversal(self, node=None):
        if node is None:
            node = self.root
        result = []
        self._inorder_helper(node, result)
        return result
    
    def _inorder_helper(self, node, result):
        if node:
            self._inorder_helper(node.left, result)
            result.append(node.value)
            self._inorder_helper(node.right, result)
                
                
    def sorted_list_to_bst(self, nums):
        self.root = self.__sorted_list_to_bst(nums, 0, len(nums) - 1)

    def __sorted_list_to_bst(self, nums, left, right):
        if left > right:
            return None
            
        mid = (left + right) // 2
        current = Node(nums[mid])
        
        current.left = self.__sorted_list_to_bst(nums, left, mid - 1)
        current.right = self.__sorted_list_to_bst(nums, mid + 1, right)
        
        return current




#  +====================================================+  
#  |  Test code below will print output to "User logs"  |
#  +====================================================+ 

def check_balanced_and_correct_traversal(bst, expected_traversal):
    is_balanced = bst.is_balanced()
    inorder = bst.inorder_traversal()
    print("Is balanced:", is_balanced)
    print("Inorder traversal:", inorder)
    print("Expected traversal:", expected_traversal)
    if is_balanced and inorder == expected_traversal:
        print("PASS: Tree is balanced and inorder traversal is correct.\n")
    else:
        print("FAIL: Tree is either not balanced or inorder traversal is incorrect.\n")

# Test: Convert an empty list
print("\n----- Test: Convert Empty List -----\n")
bst = BinarySearchTree()
bst.sorted_list_to_bst([])
check_balanced_and_correct_traversal(bst, [])

# Test: Convert a list with one element
print("\n----- Test: Convert Single Element List -----\n")
bst = BinarySearchTree()
bst.sorted_list_to_bst([10])
check_balanced_and_correct_traversal(bst, [10])

# Test: Convert a sorted list with odd number of elements
print("\n----- Test: Convert Sorted List with Odd Number of Elements -----\n")
bst = BinarySearchTree()
bst.sorted_list_to_bst([1, 2, 3, 4, 5])
check_balanced_and_correct_traversal(bst, [1, 2, 3, 4, 5])

# Test: Convert a sorted list with even number of elements
print("\n----- Test: Convert Sorted List with Even Number of Elements -----\n")
bst = BinarySearchTree()
bst.sorted_list_to_bst([1, 2, 3, 4, 5, 6])
check_balanced_and_correct_traversal(bst, [1, 2, 3, 4, 5, 6])

# Test: Convert a large sorted list
print("\n----- Test: Convert Large Sorted List -----\n")
bst = BinarySearchTree()
large_sorted_list = list(range(1, 16))  # A list from 1 to 15
bst.sorted_list_to_bst(large_sorted_list)
check_balanced_and_correct_traversal(bst, large_sorted_list)
```

### 6.  Invert Binary Tree
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
        elif value > current_node.value:  # Changed to elif to avoid comparing twice if equal
            current_node.right = self.__r_insert(current_node.right, value) 
        return current_node    

    def r_insert(self, value):
        if self.root == None: 
            self.root = Node(value)
        else:
            self.__r_insert(self.root, value)  

    def invert(self):
        self.root = self.__invert_tree(self.root)

    def __invert_tree(self, node):
        if node is None:
            return None
    
        temp = node.left
        node.left = self.__invert_tree(node.right)
        node.right = self.__invert_tree(temp)
        
        return node




#  +====================================================+  
#  |  Test code below will print output to "User logs"  |
#  +====================================================+ 

def tree_to_list(node):
    """Helper function to convert tree to list level-wise for easy comparison"""
    if not node:
        return []
    queue = [node]
    result = []
    while queue:
        current = queue.pop(0)
        if current:
            result.append(current.value)
            queue.append(current.left)
            queue.append(current.right)
        else:
            result.append(None)
    while result and result[-1] is None:  # Clean up trailing None values
        result.pop()
    return result

def test_invert_binary_search_tree():
    print("\n--- Testing Inversion of Binary Search Tree ---")
    # Define test scenarios
    scenarios = [
        ("Empty Tree", [], []),
        ("Single Node", [1], [1]),
        ("Tree with Left Child", [2, 1], [2, None, 1]),
        ("Tree with Right Child", [1, 2], [1, 2]),
        ("Multi-Level Tree", [3, 1, 5, 2], [3, 5, 1, None, None, 2]),
        ("Invert Twice", [4, 2, 6, 1, 3, 5, 7], [4, 2, 6, 1, 3, 5, 7]),
    ]

    for description, setup, expected in scenarios:
        bst = BinarySearchTree()
        for num in setup:
            bst.r_insert(num)
        if description == "Invert Twice":
            bst.invert()  # First inversion
        bst.invert()  # Perform inversion (or second inversion for the specific case)
        result = tree_to_list(bst.root)
        print(f"\n{description}: {'Pass' if result == expected else 'Fail'}")
        print(f"Expected: {expected}")
        print(f"Actual:   {result}")

test_invert_binary_search_tree()
```
