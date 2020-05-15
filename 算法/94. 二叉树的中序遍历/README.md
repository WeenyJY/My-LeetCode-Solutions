| [English](README_EN.md) | 简体中文 |

# [94. 二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal)
<p>给定一个二叉树，返回它的<em>中序&nbsp;</em>遍历。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,null,2,3]
   1
    \
     2
    /
   3

<strong>输出:</strong> [1,3,2]</pre>

<p><strong>进阶:</strong>&nbsp;递归算法很简单，你可以通过迭代算法完成吗？</p>

**标签:**  [栈](https://leetcode-cn.com/tag/stack) [树](https://leetcode-cn.com/tag/tree) [哈希表](https://leetcode-cn.com/tag/hash-table) 
 ### 相似题目
- 中等:	[验证二叉搜索树](https://leetcode-cn.com/problems/validate-binary-search-tree) 
- 中等:	[二叉树的前序遍历](https://leetcode-cn.com/problems/binary-tree-preorder-traversal) 
- 困难:	[二叉树的后序遍历](https://leetcode-cn.com/problems/binary-tree-postorder-traversal) 
- 中等:	[二叉搜索树迭代器](https://leetcode-cn.com/problems/binary-search-tree-iterator) 
- 中等:	[二叉搜索树中第K小的元素](https://leetcode-cn.com/problems/kth-smallest-element-in-a-bst) 
- 困难:	[最接近的二叉搜索树值 II](https://leetcode-cn.com/problems/closest-binary-search-tree-value-ii) 
- 中等:	[二叉搜索树中的顺序后继](https://leetcode-cn.com/problems/inorder-successor-in-bst) 
- 中等:	[将二叉搜索树转化为排序的双向链表](https://leetcode-cn.com/problems/convert-binary-search-tree-to-sorted-doubly-linked-list) 
- 简单:	[二叉搜索树节点最小距离](https://leetcode-cn.com/problems/minimum-distance-between-bst-nodes) 

# 解题思路 √

### Python

1. 递归

```python
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:return []
        self.result=[]

        def dfs(root):
            if root:
                dfs(root.left)
                self.result.append(root.val)
                dfs(root.right)
        
        dfs(root)
        return self.result
```

2. 中序遍历只要写过一次就可以记住了

   [LeetCode官方图解](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/solution/er-cha-shu-de-zhong-xu-bian-li-by-leetcode/)


```python
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:return []

        self.result=[]
        stack=[]
        currNode=root
        while currNode or stack:
            while currNode:
                stack.append(currNode)
                currNode=currNode.left
            node=stack.pop()
            self.result.append(node.val)
            currNode=node.right
        return self.result
```

3. 颜色标记法-类似当初课堂上学到的标记次数
   - 使用颜色标记节点的状态，新节点为白色，已访问的节点为灰色。
   - 如果遇到的节点为白色，则将其标记为灰色，然后将其右子节点、自身、左子节点依次入栈。
   - 如果遇到的节点为灰色，则将节点的值输出。

```python
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:return []
        self.result=[]

        stack=[(root,0)]
        while stack:
            node,times=stack.pop()
            if not node:continue
            if times==0:
                stack.append((node.right,0))
                stack.append((node,1))
                stack.append((node.left,0))
            if times==1:
                self.result.append(node.val)
        return self.result
```



### C++

```cpp

```

---



# 整理与总结

1. 中序遍历

   ```
   栈S;
   p= root;
   while(p || S不空){
       while(p){
           p入S;
           p = p的左子树;
       }
       p = S.top 出栈;
       访问p;
       p = p的右子树;
   }
   ```

   