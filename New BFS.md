651 · Binary Tree Vertical Order Traversal
```java
public class Solution {
    /**
     * @param root the root of binary tree
     * @return the vertical order traversal
     */
    public List<List<Integer>> verticalOrder(TreeNode root) {
        // Write your code here
        List<List<Integer>> ans = new ArrayList<>();
        if (root == null) {
            return ans;
        }

        Map<Integer, List<Integer>> hash = new HashMap<>();
        Queue<Integer> qCol = new LinkedList<>();
        Queue<TreeNode> qNode = new LinkedList<>();

        qCol.offer(0);
        qNode.offer(root);

        while (!qCol.isEmpty()) {
            int c = qCol.poll();
            TreeNode node = qNode.poll();

            hash.putIfAbsent(c, new ArrayList<>());
            hash.get(c).add(node.val);

            if (node.left != null) {
                qCol.offer(c - 1);
                qNode.offer(node.left);
            }
            if (node.right != null) {
                qCol.offer(c + 1);
                qNode.offer(node.right);
            }
        }

        for (int i = Collections.min(hash.keySet()); i <= Collections.max(hash.keySet()); i++) {
            ans.add(hash.get(i));
        }
        return ans;
    }
}

```
71 · Binary Tree Zigzag Level Order Traversal
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
public class Solution
{
    /**
     * @param root: A Tree
     * @return: A list of lists of integer include the zigzag level order traversal of its nodes' values.
     */
    public List<List<Integer>> zigzagLevelOrder(TreeNode root){
        List<List<Integer>> ans = new ArrayList<List<Integer>>();
        if (root == null) {
            return ans;
        }
        Queue<TreeNode> q = new LinkedList<TreeNode>();
        boolean isForward = true;
        q.offer(root);
        while (!q.isEmpty()) {
            int size = q.size();
            List<Integer> subList = new ArrayList<Integer>();
            for (int i = 0 ; i < size ; i++) {
                TreeNode treeNode = q.poll();
                subList.add(treeNode.val);
                if (treeNode.left != null) { 
                    q.offer(treeNode.left);
                }
                if (treeNode.right != null) {
                    q.offer(treeNode.right);
                }
            }
            if (!isForward) {
                Collections.reverse(subList);
            }
            ans.add(subList);
            isForward = !isForward;
        }
        return ans;
    }
}

```
480 · Binary Tree Paths
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
     * @param root the root of the binary tree
     * @return all root-to-leaf paths
     */
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> paths = new ArrayList<>();
        if (root == null) {
            return paths;
        }
        
        List<String> leftPaths = binaryTreePaths(root.left);
        List<String> rightPaths = binaryTreePaths(root.right);
        for (String path : leftPaths) {
            paths.add(root.val + "->" + path);
        }
        for (String path : rightPaths) {
            paths.add(root.val + "->" + path);
        }

        if (paths.size() == 0) {
            paths.add("" + root.val);
        }
        
        return paths;
    }
}

```
155 · Minimum Depth of Binary Tree
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

```