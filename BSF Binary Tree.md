BSF Binary Tree

LintCode 71
Binary Tree Zigzag Level Order Traversal

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
        List<List<Integer>>result = new ArrayList<List<Integer>>();
        // 创建 result 储存结果
        if (root == null) {
            return result;
        }
        Deque<TreeNode> queue = new LinkedList<TreeNode>();
        // 创建需要的数据结构Deque（可以从队首或队尾添加，也可以从队首和队尾取出）
        queue.offerLast(root);
        // 因为是queue，所以要后进先出 offer.last
        boolean isFromRight = false;
        // 初始化flag 为 0
        while (!queue.isEmpty()) {
            // 只要 queue 不为空，就可以进入
            int size = queue.size();
            // 先提取size 就知道forloop 要跑几次
            List<Integer> list = new ArrayList<Integer>();
            // 给list 赋值
            for (int i = 0 ; i < size ; i++) {
                if (isFromRight == false) {
                    // flag = false 属于正常情况
                    TreeNode node = queue.pollFirst();
                    // 正常情况就是后进先出，所以pollFirst
                    list.add(node.val);
                    if (node.left != null) {
                        queue.offerLast(node.left);
                        // 先加左侧node
                    }
                    if (node.right != null) {
                        queue.offerLast(node.right);
                        // 再加右侧node
                    }
                } else { 
                    TreeNode node = queue.pollLast();
                    // 异常情况下 先进后出
                    list.add(node.val);
                    if (node.right != null) {
                        queue.offerFirst(node.right);
                        // 先加右侧node
                    }
                    if (node.left != null) {
                        queue.offerFirst(node.left);
                        // 再加左侧node
                    }
                }
            } // 分层，一轮跑完

            // comments
            /*
            asdfasd
            asdfasdf
            */
            isFromRight = flipTraversalDirection(isFromRight);  // comments
            // reverse flag
            result.add(list);
            // 把当前层的答案加入result
        }
        return result;
    }

    private boolean flipTraversalDirection(boolean flag) {
        return !flag;
    }
}
```


leet