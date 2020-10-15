## 二叉树的最大深度
    给定一个二叉树，找出其最大深度。

    二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

    说明: 叶子节点是指没有子节点的节点。
#### 示例1
    给定二叉树 [3,9,20,null,null,15,7]，
       3
      / \
      9  20
        /  \
      15   7
    返回它的最大深度 3 。
#### 思路
  * 标签：DFS
  * 找出终止条件：当前节点为空
  * 找出返回值：节点为空时说明高度为 0，所以返回 0；节点不为空时则分别求左右子树的高度的最大值，同时加1表示当前节点的高度，返回该数值
  * 某层的执行过程：在返回值部分基本已经描述清楚
  * 时间复杂度：O(n)
#### 答案
```  javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var maxDepth = function(root) {
    if(!root) {
      return 0;
    } else {
      const left = maxDepth(root.left);
      const right = maxDepth(root.right);
      return Math.max(left, right) + 1;
    }
};
```