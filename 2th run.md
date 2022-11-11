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
        // write your code here
        if (root == null) {
            return 0;
        }
        int leftDepth = minDepth(root.left);
        int rightDepth = minDepth(root.right); 

        if (leftDepth == 0 || rightDepth == 0) {
            return leftDepth + rightDepth + 1;
        }
        return Math.min(leftDepth ,rightDepth) + 1;
    }
}
```

97 · Maximum Depth of Binary Tree
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

        return Math.max(leftDepth, rightDepth) + 1;
    }
}

```

469 · Same Tree
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
     * @param a: the root of binary tree a.
     * @param b: the root of binary tree b.
     * @return: true if they are identical, or false.
     */
    public boolean isIdentical(TreeNode a, TreeNode b) {
        // write your code here
        if (a == null && b == null) {
            return true;
        }
        if (a == null || b == null ) {
            return false;
        }
        if (a.val == b.val) {
            return isIdentical(a.left, b.left) && isIdentical(a.right,b.right);
        }
        else {
            return false;
        }
    }
}


```

470 · Tweaked Identical Binary Tree
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
     * @param a: the root of binary tree a.
     * @param b: the root of binary tree b.
     * @return: true if they are tweaked identical, or false.
     */
    public boolean isTweakedIdentical(TreeNode a, TreeNode b) {
        // write your code here
        if (a == null && b == null) {
            return true;
        }
        if (a == null || b == null) {
            return false;
        }
        if (a.val != b.val) {
            return false;
        }
        if (isTweakedIdentical(a.left,b.left) && isTweakedIdentical(a.right,b.right)) {
            return true;
        }
        if (isTweakedIdentical(a.left, b.right) && isTweakedIdentical(a.right,b.left)) {
            return true;
        }
        return false;
    }
}

```

1360 · Symmetric Tree
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
    }
    private boolean mirror(TreeNode left, TrbreeeNode right) {
        if (left == null && right == null){
           return true; 
        }
    	if (left == null || right == null) {
            return false;
        }
	    if (left.val != right.val) {
            return false;
        }
	    return mirror(left.left, right.right) && mirror(left.right, right.left);
    }
}`

```

175 · Invert Binary Tree
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
     * @param root: a TreeNode, the root of the binary tree
     * @return: nothing
     */
    public void invertBinaryTree(TreeNode root) {
        // write your code here
        if (root == null) {
            return;
        }
        TreeNode temp = root.left;
        root.left = root.right; 
        root.right = temp;

        invertBinaryTree(root.left);
        invertBinaryTree(root.right);

    }
}

```
95 · Validate Binary Search Tree
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
        // write your code here
        return isValidBST(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }
    public boolean isValidBST(TreeNode node, long min, long max){
        if (node == null) {
            return true;
        }
        if (node.val <= min || node.val >= max) {
            return false;
        } 
        return isValidBST(node.left, min, node.val) && isValidBST(node.right, node.val, max);
    }
}
```
66 · Binary Tree Preorder Traversal
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
     * @return: Preorder in ArrayList which contains node values.
     */
    public List<Integer> preorderTraversal(TreeNode root) {
        // write your code here
        List<Integer> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        List left = preorderTraversal(root.left);
        List right = preorderTraversal(root.right);

        result.add(root.val);
        result.addAll(left);
        result.addAll(right);

        return result;
    }
}

```
67 · Binary Tree Inorder Traversal
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
     * @return: Inorder in ArrayList which contains node values.
     */
    public List<Integer> inorderTraversal(TreeNode root) {
        // write your code here

        List<Integer> result = new Arraylist<>();
        if (root == null) {
            return result;
        }
        List left = inorderTraversal(root.left);
        List right = inorderTraversal(root.right);

        result.addAll(left);
        result.add(root.val);
        result.addAll(right);
    }
}
```
68 · Binary Tree Postorder Traversal
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
     * @return: Inorder in ArrayList which contains node values.
     */
    public List<Integer> postorderTraversal(TreeNode root) {
        // write your code here
        List<Integer> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        List left = postorderTraversal(root.left);
        List right = postorderTraversal(root.right);

        result.addAll(left);
        result.addAll(right);
        result.add(root.val);
       
       return result;
    }
}

```
 Binary Tree Preorder Traversal
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
     * @return: Preorder in ArrayList which contains node values.
     */
    public List<Integer> preorderTraversal(TreeNode root) {
        // write your code here
        Stack<TreeNode> stack = new Stack<TreeNode>();
        List<Integer> result = new ArrayList<Integer>();
        if (root == null) {
            return result;
        }
        stack.push(root);
        while (!stack.isEmpty()) {
            TreeNode node = stack.pop();
            result.add(node.val);
            if (node.right != null) {
                stack.push(node.right);
            }
            if (node.left != null) {
                stack.push(node.left);
            }
        } 
        return result;
    }
}

```
Binary Tree Inorder Traversal
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
     * @return: Inorder in ArrayList which contains node values.
     */
    public List<Integer> inorderTraversal(TreeNode root) {
        // write your code here
        Stack<TreeNode> stack = new Stack<TreeNode>();
        List<Integer> result = new ArrayList<Integer>();

        TreeNode node = root;
        while (node != null || !stack.empty()) {
            while (node != null) {
                stack.push(node);
                node = node.left;
            }
            node = stack.pop();
            result.add(node.val);
            node = node.right;
        }
        return result;
    }
}
```
Binary Tree Postorder Traversal

```java
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        Stack<TreeNode> stack = new Stack<>();
        List<Integer> result = new ArrayList<>();

        TreeNode prev = null;
        TreeNode curr = root;
        
        if (root == null) {
            return result;
        }
        stack.push(root);
        while (!stack.isEmpty()) {
            curr = stack.peek();
            if (prev == null || prev.left == curr || prev.right == curr) {
                if (curr.left != null) {
                    stack.push(curr.left);
                } else if (curr.right != null) {
                    stack.push(curr.right);
                }
            } else if (curr.left == prev) {
                if (curr.right != null) {
                    stack.push(curr.right);
                }
            } else {
                result.add(curr.val);
                stack.pop();
            }
            prev = curr;
        }
        return result;
    }
}
```
93 · Balanced Binary Tree

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
     * @return: True if this Binary tree is Balanced, or false.
     */
    public boolean isBalanced(TreeNode root) {
        // write your code here
        return getMaxDpeth(root) >= 0;
    }
    private int getMaxDpeth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        int heightLeft = getMaxDpeth(root.left);
        int heightRight = getMaxDpeth(root.right);

        if (heightLeft == -1 || heightRight == -1 || Math.abs(heightLeft - heightRight) > 1) {
            return -1;
        } else {
            return Math.max(heightLeft, heightRight) + 1;
        }
    }
}

```
177 · Convert Sorted Array to Binary Search Tree With Minimal Height.

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
     * @param a: an integer array
     * @return: A tree node
     */
    public TreeNode sortedArrayToBST(int[] a) {
        // write your code here
        if (a == null) {
            return null;
        }
        return buildTree(a, 0, a.length - 1);
    }
    
    private TreeNode buildTree(int[] a, int start, int end) {
        if (start > end) {
            return null;
        }
        
        TreeNode node = new TreeNode(a[(start + end) / 2]);
        node.left = buildTree(a, start, (start + end) / 2 - 1);
        node.right = buildTree(a, (start + end) / 2 + 1, end);
        return node;
    }
}

```

1704 · Range Sum of BST
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
     * @param root: the root node
     * @param l: an integer
     * @param r: an integer
     * @return: the sum
     */
     int result = 0;
    public int rangeSumBST(TreeNode root, int l, int r) {
        // write your code here.
        helper(root, l, r);
        return result;
    }
    private void helper(TreeNode root, int min, int max) {
        if (root == null) {
            return;
        }
        if (root.val > min) {
            helper(root.left, min, max);
        }
        if (root.val >= min && root.val <= max) {
            result += root.val;
        }
        if (root.val < max) {
            helper(root.right, min, max);
        }
    }
}

```

1534 · Convert Binary Search Tree to Sorted Doubly Linked List
```java



class Solution {

  TreeNode first = null;
  TreeNode last = null;

  public void helper(TreeNode node) {
    if (node != null) {
      helper(node.left);
      if (last != null) {
        last.right = node;
        node.left = last;
      }
      else {
        first = node;
      }
      last = node;
      helper(node.right);
    }
  }

  public TreeNode treeToDoublyList(TreeNode root) {
    if (root == null) return null;

    helper(root);
    last.right = first;
    first.left = last;
    return first;
  }
}

```

1311 · Lowest Common Ancestor of a Binary Search Tree

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
     * @param root: root of the tree
     * @param p: the node p
     * @param q: the node q
     * @return: find the LCA of p and q
     */
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        // write your code here
        int pVal = p.val;
        int qVal = q.val;
        
        TreeNode node = root;
        while (node != null) {
            int parentVal = node.val;
            if (pVal > parentVal && qVal > parentVal) {
                node = node.right;
            } else if (pVal < parentVal && qVal < parentVal) {
                node = node.left;
            } else {
                return node;
            }
        }
        return null;
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
     * @param root: the root of the binary tree
     * @return: all root-to-leaf paths
     *          we will sort your return value in output
     */
    public List<String> binaryTreePaths(TreeNode root) {
        // write your code here
        List<String> result = new ArrayList<>();
        helper(root, "", result);
        return result;
    }
    private void helper(TreeNode root, String save, List<String> result) {
        if (root == null) {
            return;
        } else {
            save = save + Integer.toString(root.val);
        }
        if (root.left == null && root.right == null) {
            result.add(save);
        } else {
            save = save + "->" ;
            helper(root.left, save, result);
            helper(root.right, save, result);
        }
    }
}

```

112 · Remove Duplicates from Sorted List
```java
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param head: head is the head of the linked list
     * @return: head of linked list
     */
    public ListNode deleteDuplicates(ListNode head) {
        // write your code here
        if (head == null) {
            return head;
        }
        ListNode node = head;
        while (node.next != null) {
            if (node.val == node.next.val) {
                node.next = node.next.next;
            } else {
                node = node.next;
            }
        }
        return head;
    }
}

```

35 · Reverse Linked List
```java
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param head: n
     * @return: The new head of reversed linked list.
     */
    public ListNode reverse(ListNode head) {
        // write your code here
        if (head == null || head.next == null) {
            return head;
        }
        ListNode current = head;
        ListNode prev = null;
        ListNode furture = null;
        while (current != null) {
            furture = current.next;
            current.next = prev;
            prev = current;
            current = furture;
        }
        return prev;
    }
}

```
228 · Middle of Linked List

```java
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param head: the head of linked list.
     * @return: a middle node of the linked list
     */
    public ListNode middleNode(ListNode head) {
        // write your code here
        if (head == null || head.next == null) {
            return head;
        }
            ListNode slow = head;
            ListNode fast = head.next;
            while (fast != null && fast.next != null) {
                slow = slow.next;
                fast = fast.next.next;
            }
            return slow;
    }
}

```

96 · Partition List
```java
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param head: The first node of linked list
     * @param x: An integer
     * @return: A ListNode
     */
    public ListNode partition(ListNode head, int x) {
        // write your code here
        
        ListNode dummy1 = new ListNode(0);
        ListNode dummy2 = new ListNode(0);
        ListNode c1 = dummy1;
        ListNode c2 = dummy2;
        ListNode current = head;

        while(current != null) {
            if (current.val < x) {
                c1.next = current;
                c1 = c1.next;
                current = current.next;
            } else {
                c2.next = current;
                c2 = c2.next;
                current = current.next;
            }
        }
        c1.next = dummy2.next;
        c2.next = null;
        return dummy1.next;
    }
}

```

1292 · Odd Even Linked List

```java
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param head: a singly linked list
     * @return: Modified linked list
     */
    public ListNode oddEvenList(ListNode head) {
        // write your code here
        if (head == null) {
            return head;
        }
        ListNode odd = head;
        ListNode even = head.next;
        ListNode evendummy = even;
        while (even != null && even.next != null) {
            odd.next = even.next;
            odd = odd.next;
            even.next = even.next.next;
            even = even.next;
        }
        odd.next = evendummy;
        return head;
    }
}

```
