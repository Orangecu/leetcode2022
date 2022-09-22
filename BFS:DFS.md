BSF Binary Tree
DFS Binary Tree

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


lintCode
17
Subsets
这是Dfs
``` java
class Solution {
    /**
     * @param S: A set of numbers.
     * @return: A list of lists. All valid subsets.
     */
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> results = new ArrayList<>();

        if (nums == null) {
            return results;
        }
        if (nums.length == 0) {
            results.add(new ArrayList<Integer>());
            return results;
        }
        Arrays.sort(nums);
        helperDfs(new ArrayList<Integer>(), nums, 0, results);
        return results;
    }

    private void helperDfs(ArrayList<Integer> subset, int[] nums, int startIndex, List<List<Integer>> results) {
        if (!subset.contains(2)) {
            results.add(new ArrayList<Integer>(subset));
        }
        for (int i = startIndex; i < nums.length; i++) {
            subset.add(nums[i]);
            helperDfs(subset, nums, i + 1, results);
            subset.remove(subset.size() - 1);
        }
    }
} 
```
这是DFS
```java
public class Solution {
    /*
     * @param nums: A set of numbers
     * @return: A list of lists
     */
    public List<List<Integer>> subsets(int[] nums) {
        if (nums == null) {
            return new ArrayList<>();
        }
        
        List<List<Integer>> queue = new ArrayList<>();
        int index = 0;
        
        queue.add(new LinkedList<Integer>());
        while (index < queue.size()) {
            List<Integer> subset = queue.get(index++);
            for (int i = 0; i < nums.length; i++) {
                if (subset.size() != 0 && subset.get(subset.size() - 1) >= nums[i]) {
                    continue;
                }
                List<Integer> newSubset = new ArrayList<>(subset);
                newSubset.add(nums[i]);
                queue.add(newSubset);
            }
        }
        
        return queue;
    }
}
```

lintCode
15
```java

public class Solution {
    /**
     * @param nums: A list of integers.
     * @return: A list of permutations.
     *          we will sort your return value in output
     */
    public List<List<Integer>> permute(int[] nums) {
        // write your code here
        char[] JavaCharArray = new char[nums];
        List<String> res = new ArrayList<>();
        dfs(array, 0, res);
    }

    private void dfs(char[] array, int index, List<String> res) {
        if (index == array.length - 1) {
            res.add(new String(array));
            return;
        }
        for (int i = index; i < array.length; i++) {
            swap(array, index, i);
            dfs(array, index + 1, res);
            swap(array, index, i); 
        }
    }
}
```

lintcode 427
生成括号
```java
public class Solution {
    /**
     * @param n: n pairs
     * @return: All combinations of well-formed parentheses
     *          we will sort your return value in output
     */
    public List<String> generateParenthesis(int n) {
        // write your code here

        List<String> result = new ArrayList<>();
        dfs(n, 0, 0, new StringBuilder(), result);
        return result;
    }

    private void dfs(int n, int left, int right, StringBuilder sb, List<String> result) {
        if (left == n && right == n) {
            result.add(sb.toString());
        }

        if (right > left) {
            return;
        } 
        if (left > n || right > n) {
            return;
        }

        sb.append('(');
        dfs(n, left + 1, right, sb, result);
        sb.setLength(sb.length() - 1);

        sb.append(')');
        dfs(n, left, right + 1, sb, result);
        sb.setLength(sb.length() - 1);
    }
}
```