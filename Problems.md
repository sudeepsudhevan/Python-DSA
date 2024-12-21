### 1. List: Remove Element
```py
def remove_element(nums, val):
    i = 0
    while i < len(nums):
        if nums[i] == val:
            nums.pop(i)
        else:
            i += 1
    return len(nums)

nums1 = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
val1 = 1
print("\nRemove a single instance of value", val1, "in the middle of the list.")
print("BEFORE:", nums1)
new_length1 = remove_element(nums1, val1)
print("AFTER:", nums1, "\nNew length:", new_length1)
print("-----------------------------------")

````
