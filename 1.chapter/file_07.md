
Q7. Why are keys important in lists, and what problems arise from using array index as a key?

A7. Keys are unique identifiers that help React recognize which items have changed, been added, or removed. They're like ID cards for list items.

"Using array index as a key is problematic because indices change when you add, remove, or reorder items. When indices change, React can't identify which item is which, leading to:

Unnecessary re-renders
State getting mixed up between items
Input values appearing on wrong items