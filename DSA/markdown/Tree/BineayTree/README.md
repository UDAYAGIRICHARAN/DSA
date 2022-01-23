Height Balanced Tree
Given the root of a binary tree, return whether its height is balanced. That is, for every node in the tree, the absolute difference of the height of its left subtree and the height of its right subtree is 0 or 1.

# class Tree:
#     def __init__(self, val, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def solve(self, root):
        isBalanced = True

        def dfs(depth, root):
            nonlocal isBalanced
            if not root:
                return depth

            left = dfs(depth + 1, root.left)
            right = dfs(depth + 1, root.right)

            if abs(left - right) > 1:
                isBalanced = False

            return max(left, right)

        dfs(0, root)
        return isBalanced
