Binary Tree Collection

LintCode
155
二叉树最小深度

```java 
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */
public class Solution {
    /**
     * @param root: The root of binary tree
     * @return: An integer
     */
    public int minDepth(TreeNode root) {
        if (root == null){
            return 0;
        }
        int leftDepth = minDepth(root.left);
        int rightDepth = minDepth(root.right);
        if (leftDepth == 0 || rightDepth == 0){
            return leftDepth + rightDepth + 1;
        }
        return Math.min(leftDepth, rightDepth) + 1;
    }
}





public bt(root k1 k2) {
    if (root = null) {
        return null;
    }
    if (k1 < left.root.val){
        left1
    }
}

```

LintCode
97
二叉树最大深度

```java
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: An integer
     */
    public int maxDepth(TreeNode root) {
        // write your code here
        if (root == null) {
            return 0;
        }
        int leftDepth = maxDepth(root.left);
        int rightDepth = maxDepth(root.right);
        return Math.max(leftDepth, rightDepth)+1;
    }
}

```

LeetCode 
470
扭转后等价二叉树

```java
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */
public class Solution {
    /**
     * @param a, b, the root of binary trees.
     * @return true if they are tweaked identical, or false.
     */
    public boolean isTweakedIdentical(TreeNode a, TreeNode b) {
        if (a == null && b == null) {
            return true;
        } //检查左右都是否null
        if (a == null || b == null) {
            return false;
        } //单边null 直接false
        if (a.val != b.val) {
            return false;
        } //a/b value不等 
        if (isTweakedIdentical(a.left, b.left) && isTweakedIdentical(a.right, b.right)) {
            return true;
        } //ab子树 左左右右检查
        
        if (isTweakedIdentical(a.left, b.right) && isTweakedIdentical(a.right, b.left)) {
            return true;
        } //ab子树 左右左右检查
        
        return false;
    }
}
```

LeetCode
100
SameTree
```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p == null && q == null) {
            return true;
        } //如果两个都是null 直接return对
        else if(p == null || q == null) {
            return false;
        } //如果一个null 一个不是，return 错，因为两边不等
        if(p.val == q.val) { //如果q的value 和 p的value一样，进入循环
            return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
        } //检查两遍的子树， 如果不一致就是false
        else{
            return false;
        }
    }
}

```

LeetCode
101
Symmetric tree
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
    public boolean isSymmetric(TreeNode root) {
        return root == null ? true : mirror(root.left, root.right);
        // 如果 root == null 返回 true， 如果不等于，则 mirror 左右
    }
    private boolean mirror(TreeNode left, TreeNode right) {
        if (left == null && right == null){
           return true; 
        } //左右null 相等
    	if (left == null || right == null) {
            return false;
        } //单null 不相等 false
	    if (left.val != right.val) {
            return false;
        } //检查左右value 
	    return mirror(left.left, right.right) && mirror(left.right, right.left);
    }   // return出 镜想的左子树left/right 右子树left/right
}
```

LeetCode
226
Invert Binary Tree
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
    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return root;
        }
        invertTree(root.left);
        invertTree(root.right);
        
        TreeNode temp = root.left;
        root.left = root.right;
        root.right = root.left;
        
        return root;
        
    }
}

```

LintCode
11
二叉查找树 搜索区间
```java
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */
public class Solution {
    private ArrayList<Integer> results;
    /**
     * @param root: The root of the binary search tree.
     * @param k1 and k2: range k1 to k2.
     * @return: Return all keys that k1<=key<=k2 in increasing order.
     */
    public ArrayList<Integer> searchRange(TreeNode root, int k1, int k2) {
        results = new ArrayList<Integer>();
        helper(root, k1, k2);
        return results;
    } //最小数k1 最大数k2 
        //从中间根节点开始找，如果根节点大于k1（最小数），就向左子树搜寻
        //如果根节点小于k2（最大数）则向右寻找
        //如果是在k1/k2之间，则将存入结果
    private void helper(TreeNode root, int k1, int k2) {
        if (root == null) {
            return;
        } //root 是 null 直接return
        
        if (root.val > k1) {
            helper(root.left, k1, k2);
        } // root大于k1 root 向左移动

        if (root.val >= k1 && root.val <= k2) {
            results.add(root.val);
        } //如果 大于等于 k1 以及 小于等于 k2，把这个root加入 结果

        
        if (root.val < k2) {
            helper(root.right, k1, k2);
        } // root小于k2 root 向右移动
    }
}


```

lintCode
95
验证二叉查找树
```java

/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: True if the binary tree is BST, or false
     */
    public boolean isValidBST(TreeNode root) {
        return isValidBST(root, Integer.MIN_VALUE, Integer.MAX_VALUE);        
    }
    private boolean isValidBST(TreeNode root, int min, int max) {
        if (root == null) {
            return true;
        } //root = null, 无剩余子树
        if (root.val >= max || root.val <= min) {
            return false;
        } // 如果 root 的值 小于 最小值 ｜｜ 或 大于 最大值 
            // return false
        return isValidBST (root.left, min, root.val) && isValidBST (root.right, root.val, max );
    }   //若不符合上一条 则 return true
}
```