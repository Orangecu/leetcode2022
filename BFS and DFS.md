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

15 · Permutations
```java
public class Solution {
    /*
     * @param nums: A list of integers.
     * @return: A list of permutations.
     */
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> results = new ArrayList<>();
        if (nums == null) {
            return results;
        }
        
        dfs(nums, new boolean[nums.length], new ArrayList<Integer>(), results);
        
        return results;
    }
    
    private void dfs(int[] nums,
                     boolean[] visited,
                     List<Integer> permutation,
                     List<List<Integer>> results) {
        if (nums.length == permutation.size()) {
            results.add(new ArrayList<Integer>(permutation));
            return;
        }
        
        for (int i = 0; i < nums.length; i++) {
            if (visited[i]) {
                continue;
            }
            
            permutation.add(nums[i]);
            visited[i] = true;
            dfs(nums, visited, permutation, results);
            visited[i] = false;
            permutation.remove(permutation.size() - 1);
        }
    }
}
```


17 · Subsets
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



69 · Binary Tree Level Order Traversal
```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> ret = new ArrayList<List<Integer>>();
        if (root == null) {
            return ret;
        }
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            List<Integer> level = new ArrayList<Integer>();
            int currentLevelSize = queue.size();
            for (int i = 1; i <= currentLevelSize; ++i) {
                TreeNode node = queue.poll();
                level.add(node.val);
                if (node.left != null) {
                    queue.offer(node.left);
                }
                if (node.right != null) {
                    queue.offer(node.right);
                }
            }
            ret.add(level);
        }
        return ret;
    }
}
```
611 · Knight Shortest Path

```java
public class Solution {
    int n, m; // size of the chessboard
    int[] deltaX = {1, 1, 2, 2, -1, -1, -2, -2};
    int[] deltaY = {2, -2, 1, -1, 2, -2, 1, -1};
    /**
     * @param grid a chessboard included 0 (false) and 1 (true)
     * @param source, destination a point
     * @return the shortest path 
     */
    public int shortestPath(boolean[][] grid, Point source, Point destination) {
        if (grid == null || grid.length == 0 || grid[0].length == 0) {
            return -1;
        }
        n = grid.length;
        m = grid[0].length;

        Queue<Point> queue = new LinkedList<>();
        queue.offer(source);
        
        int steps = 0;
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                Point point = queue.poll();
                if (point.x == destination.x && point.y == destination.y) {
                    return steps;
                }
                
                for (int direction = 0; direction < 8; direction++) {
                    Point nextPoint = new Point(
                        point.x + deltaX[direction],
                        point.y + deltaY[direction]
                    );
                    
                    if (!inBound(nextPoint, grid)) {
                        continue;
                    }
                    
                    queue.offer(nextPoint);
                    // mark the point not accessible
                    grid[nextPoint.x][nextPoint.y] = true;
                }
            }
            steps++;
        }
        
        return -1;
    }
    
    private boolean inBound(Point point, boolean[][] grid) {
        if (point.x < 0 || point.x >= n) {
            return false;
        }
        if (point.y < 0 || point.y >= m) {
            return false;
        }
        return (grid[point.x][point.y] == false);
    }
}

```
69 · Binary Tree Level Order Traversal

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
     * @param root: A Tree
     * @return: Level order a list of lists of integer
     */
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        Queue<TreeNode> queue = new ArrayDeque<>();
        
        if (root == null) {
            return null;
        }

        queue.offer(root);

        while (!queue.isEmpty()) {
            List<Integer> level = new ArrayList<>();
            int size = queue.size();

            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                level.add(node.val);

                if (node.left != null) {
                    queue.offer(node.left);
                }
                if (node.right != null) {
                    queue.offer(node.right);
                }
            }

            result.add(level);
        }

        return result;
    }
}

```

70 · Binary Tree Level Order Traversal II
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
     * @param root: A tree
     * @return: buttom-up level order a list of lists of integer
     */
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        // write your code here
        List<List<Integer>> result = new ArrayList<>();
        LinkedList<TreeNode> queue = new LinkedList<>();

        if (root != null) {
            queue.offer(root);
        }
        while (!queue.isEmpty()) {
            int length = queue.size();
            List<Integer> tempList = new ArrayList<>();

            while (length > 0) {
                TreeNode treeNode = queue.poll();
                tempList.add(treeNode.val);
                if (treeNode.left != null) {
                    queue.offer(treeNode.left);
                }
                if (treeNode.right != null) {
                    queue.offer(treeNode.right);
                }
                length--;
            }
            result.add(tempList);
        }
        Collections.reverse(result);
        return result;
    }
}

```
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

public class Solution {
    /**
     * @param root: A Tree
     * @return: A list of lists of integer include the zigzag level order traversal of its nodes' values.
     */
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        // write your code here
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) {
            return null;
        }
        Deque<TreeNode> queue = new LinkedList<TreeNode>();
        queue.offerLast(root);

        Boolean isFromRight = false;

        while (!queue.isEmpty()) {
            int size = queue.size();
            List<Integer> list = new ArrayList<Integer>();
            
            for (int i = 0; i < size; i++) {
                if (isFromRight == false) {
                    TreeNode node = queue.pollFirst();
                    list.add(node.val);
                    if (node.left != null) {
                        queue.offerLast(node.left);
                    }
                    if (node.left != null) {
                        queue.offerFirst(node.left);
                    }
                }
            }
            isFromRight = flipTraversalDirection(isFromRight); 
            result.add(list);
        }
        return result;
    }
    private boolean flipTraversalDirection(boolean flag) {
        return !flag;
    }
}

```
178 · Graph Valid Tree

```java

public class Solution {
    /**
     * @param n an integer
     * @param edges a list of undirected edges
     * @return true if it's a valid tree, or false
     */
    public boolean validTree(int n, int[][] edges) {
        if (n == 0) {
            return false;
        }
        if (edges.length != n - 1) {
            return false;
        }
        Map<Integer, Set<Integer>> graph = initializeGraph(n, edges);

        Queue<Integer> queue = new LinkedList<>();
        Set<Integer> hash = new HashSet<>();
        
        queue.offer(0);
        hash.add(0);
        while (!queue.isEmpty()) {
            int node = queue.poll();
            for (Integer neighbor : graph.get(node)) {
                if (hash.contains(neighbor)) {
                    continue;
                }
                hash.add(neighbor);
                queue.offer(neighbor);
            }
        }
        
        return (hash.size() == n);
    }
    
    private Map<Integer, Set<Integer>> initializeGraph(int n, int[][] edges) {
        Map<Integer, Set<Integer>> graph = new HashMap<>();
        for (int i = 0; i < n; i++) {
            graph.put(i, new HashSet<Integer>());
        }
        
        for (int i = 0; i < edges.length; i++) {
            int u = edges[i][0];
            int v = edges[i][1];
            graph.get(u).add(v);
            graph.get(v).add(u);
        }
        
        return graph;
    }
}

```
595 · Binary Tree Longest Consecutive Sequence

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
     * @param root: the root of binary tree
     * @return: the length of the longest consecutive sequence path
     */
    private int longest = 0;
    public int longestConsecutive(TreeNode root) {
        // write your code here
        helper(root, null, 0);
        return longest;
    }
    private void helper(TreeNode root, TreeNode parent, int longestSubTree) {
        if (root == null) {
            return;
        }
        if (parent != null && root.val != parent.val + 1){
            longestSubTree++;
        } else {
            longestSubTree = 1;
        }

        longest = Math.max(longest, longestSubTree);
        helper(root.left, root, longestSubTree);
        helper(root.right, root, longestSubTree);
    }
}

```