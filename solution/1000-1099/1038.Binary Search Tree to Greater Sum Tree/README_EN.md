# [1038. Binary Search Tree to Greater Sum Tree](https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree)

[中文文档](/solution/1000-1099/1038.Binary%20Search%20Tree%20to%20Greater%20Sum%20Tree/README.md)

## Description

<p>Given the <code>root</code> of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.</p>

<p>As a reminder, a <em>binary search tree</em> is a tree that satisfies these constraints:</p>

<ul>
	<li>The left subtree of a node contains only nodes with keys&nbsp;<strong>less than</strong>&nbsp;the node&#39;s key.</li>
	<li>The right subtree of a node contains only nodes with keys&nbsp;<strong>greater than</strong>&nbsp;the node&#39;s key.</li>
	<li>Both the left and right subtrees must also be binary search trees.</li>
</ul>

<p><strong>Note:</strong> This question is the same as 538:&nbsp;<a href="https://leetcode.com/problems/convert-bst-to-greater-tree/">https://leetcode.com/problems/convert-bst-to-greater-tree/</a></p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<img alt="" src="https://cdn.jsdelivr.net/gh/doocs/leetcode@main/solution/1000-1099/1038.Binary%20Search%20Tree%20to%20Greater%20Sum%20Tree/images/tree.png" style="width: 550px; height: 375px;" />

<pre>

<strong>Input:</strong> root = [4,1,6,0,2,5,7,null,null,null,3,null,null,null,8]

<strong>Output:</strong> [30,36,21,36,35,26,15,null,null,null,33,null,null,null,8]

</pre>

<p><strong>Example 2:</strong></p>

<pre>

<strong>Input:</strong> root = [0,null,1]

<strong>Output:</strong> [1,null,1]

</pre>

<p><strong>Example 3:</strong></p>

<pre>

<strong>Input:</strong> root = [1,0,2]

<strong>Output:</strong> [3,3,2]

</pre>

<p><strong>Example 4:</strong></p>

<pre>

<strong>Input:</strong> root = [3,2,4,1]

<strong>Output:</strong> [7,9,4,10]

</pre>

<p>&nbsp;</p>

<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 100</code></li>
	<li>All the values in the tree are <strong>unique</strong>.</li>
	<li><code>root</code> is guaranteed to be a valid binary search tree.</li>
</ul>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    add = 0

    def bstToGst(self, root: TreeNode) -> TreeNode:
        if root:
            self.bstToGst(root.right)
            root.val += self.add
            self.add = root.val
            self.bstToGst(root.left)
        return root
```

### **Java**

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int add = 0;
    public TreeNode bstToGst(TreeNode root) {
        if (root != null) {
            bstToGst(root.right);
            root.val += add;
            add = root.val;
            bstToGst(root.left);
        }
        return root;
    }
}
```

### **C++**

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int add = 0;
    TreeNode* bstToGst(TreeNode* root) {
        if (root) {
            bstToGst(root->right);
            root->val += add;
            add = root->val;
            bstToGst(root->left);
        }
        return root;
    }
};
```

### **Go**

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func bstToGst(root *TreeNode) *TreeNode {
	add := 0
	var dfs func(*TreeNode)
	dfs = func(node *TreeNode) {
		if node != nil {
			dfs(node.Right)
			node.Val += add
			add = node.Val
			dfs(node.Left)
		}
	}
	dfs(root)
	return root
}
```

### **...**

```

```

<!-- tabs:end -->
