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