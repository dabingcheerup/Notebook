![](/assets/Screen Shot 2018-04-21 at 10.03.39 PM.png)

####Idea_Python:
CC: root == None, return True
else return helper(root.left, root.right)

helper(left, right)
CC: 
    if left is None and right is None, return True
    if left is None or right is None, return False
    if left.val == right.val:
        return helper(left.left, right.right) and helper(left.right, right.left)
    else: return Fasle
    
    

####Code_py
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if root is None:
            return True
        else:
            return self.isMirror(root.left, root.right) # self.isMirror
        
    def isMirror(self, l, r):
        if l is None and r is None:
            return True
        if l is None or r is None:
            return False
        if l.val == r.val:
            return self.isMirror(l.left, r.right) and self.isMirror(l.right, r.left)
        else: return False
    
    
```

####Code_java


```
public boolean isSymmetric(TreeNode root) {
    return root==null || isSymmetricHelp(root.left, root.right);
}

private boolean isSymmetricHelp(TreeNode left, TreeNode right){
    if(left==null || right==null)
        return left==right;
    if(left.val!=right.val)
        return false;
    return isSymmetricHelp(left.left, right.right) && isSymmetricHelp(left.right, right.left);
}

```

