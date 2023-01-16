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
102 · Linked List Cycle

```java

public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        }
        ListNode fast;
        ListNode slow;
        fast = head;
        slow = head;
        do {
            if (fast == null || fast.next == null) {
                return false;
            }
            fast = fast.next.next;
            slow = slow.next;
        } while (fast != slow);
        
        return true;
    }
}
```

165 · Merge Two Sorted Lists
```java
//**
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
     * @param l1: ListNode l1 is the head of the linked list
     * @param l2: ListNode l2 is the head of the linked list
     * @return: ListNode head of linked list
     */
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        // write your code here
        if (l1 == null) {
            return l2;
        } else if (l2 == null) {
            return l1;
        } else if (l1.val < l2.val) {
            l1.next = mergeTwoLists(l1.next ,l2);
            return l1;
        } else {
            l2.next = mergeTwoLists(l1, l2.next);
            return l2;
        }
    }
}

```
380 · Intersection of Two Linked Lists

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
     * @param headA: the first list
     * @param headB: the second list
     * @return: a ListNode
     */
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        // write your code here
        if (headA == null || headB == null) {
            return null;
        }
        ListNode pA = headA;
        ListNode pB = headB;
        while (pA != pB) {
            pA = pA == null ? headB : pA.next;
            pB = pB == null ? headA : pB.next;
        }
        return pA;
    }
}

```
511 · Swap Two Nodes in Linked List

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
     * @param head: a ListNode
     * @param v1: An integer
     * @param v2: An integer
     * @return: a new head of singly-linked list
     */
    public ListNode swapNodes(ListNode head, int v1, int v2) {
        // write your code here
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode prev1 = dummy;
        ListNode prev2 = dummy;

        while (prev1.next != null && prev1.next.val != v1) {
            prev1 = prev1.next;
        }
        while (prev2.next != null && prev2.next.val != v2) {
            prev2 = prev2.next;
        }
        if (prev1.next == null || prev2.next == null){
            return head;
        }
        ListNode node1 = prev1.next;
        ListNode node2 = prev2.next;
        prev1.next = prev2.next;
        prev2.next = node1;
        ListNode temp = node1.next;
        node1.next = node2.next;
        node2.next = temp;
        return dummy.next;
    }
}
```

99 · Reorder List

```java
class Solution {
    public void reorderList(ListNode head) {
        if (head == null) {
            return;
        }
        ListNode mid = middleNode(head);
        ListNode l1 = head;
        ListNode l2 = mid.next;
        mid.next = null;
        l2 = reverseList(l2);
        mergeList(l1, l2);
    }

    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }

    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        ListNode next = null;
        while (curr != null) {
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }

    public void mergeList(ListNode l1, ListNode l2) {
        ListNode l1_tmp;
        ListNode l2_tmp;
        while (l1 != null && l2 != null) {
            l1_tmp = l1.next;
            l2_tmp = l2.next;

            l1.next = l2;
            l1 = l1_tmp;

            l2.next = l1;
            l2 = l2_tmp;
        }
    }
}


```

539 · Move Zeroes

```java

public class Solution {
    /**
     * @param nums: an integer array
     * @return: nothing
     */
    public void moveZeroes(int[] nums) {
        // write your code here
        int ZP = 0;
        int NZP = 0;
        while (NZP < nums.length) {
            if (nums[NZP] != 0) {
                if (ZP != NZP) {
                    nums[ZP] = nums[NZP];
                }
                ZP++;
            }
            NZP++;
        }
        while (ZP < nums.length) {
            nums[ZP++] = 0;
        }
    }
}


```
608 · Two Sum II - Input array is sorted
```java
public class Solution {
    /**
     * @param nums: an array of Integer
     * @param target: target = nums[index1] + nums[index2]
     * @return: [index1 + 1, index2 + 1] (index1 < index2)
     */
    public int[] twoSum(int[] nums, int target) {
        // write your code here
        if (nums == null || nums.length < 2) {
            return new int[] {-1, -1};
        }
        int start = 0;
        int end = nums.length -1;
        while (start < end) {
            if (nums[start] + nums[end] == target) {
                return new int[] {start + 1, end + 1};
            }
            if (nums[start] + nums[end] < target) {
                start++;
            } else {
                end--;
            }
        }
        return new int[]{-1, -1};
    }
}

```
609 · Two Sum - Less than or equal to target

```java
public class Solution {
    /**
     * @param nums: an array of integer
     * @param target: an integer
     * @return: an integer
     */
    public int twoSum5(int[] nums, int target) {
        // write your code here
        if (nums == null) {
            return 0;
        }
        Arrays.sort(nums);
        int left = 0;
        int right = nums.length - 1;
        int count = 0;
        while (left < right) {
            if (nums[left] + nums[right] <= target) {
                count += right - left;
                left++;
            } else {
                right--;
            }
        }
        return count;
    }
}

```
443 · Two Sum - Greater than target

```java
public class Solution {
    /**
     * @param nums: an array of integer
     * @param target: An integer
     * @return: an integer
     */
    public int twoSum2(int[] nums, int target) {
        // write your code here
        if ( nums == null) {
            return 0;
        }
        Arrays.sort(nums);
        int left = 0;
        int right = nums.length - 1;
        int count = 0;
        while (left < right) {
            if (nums[left] + nums[right] <= target) {
                left++;
            } else {
                count += right - left;
                right--;
            }
        }
        return count;
    }
}

```
148 · Sort Colors

```java
public class Solution {
    /**
     * @param nums: A list of integer which is 0, 1 or 2
     * @return: nothing
     */
    public void sortColors(int[] nums) {
        // write your code here
        int left = 0;
        int right = nums.length - 1;
        int mid = 0;

        while (mid <= right) {
            if (nums[mid] == 0) {
                swap(nums, mid, left);
                mid++;
                left++;
            } 
            else if (nums[mid] == 2) {
                swap(nums, mid, right);
                right--;
            }
            else {
                mid++;
            }
        }
    }
    private void swap(int[] a, int i, int j) {
        int temp = a[i];
        a[i] = a[j];
        a[j] = temp;
    }
}

```
464 · Sort color II

```java
public class Solution {
    /**
     * @param colors: A list of integer
     * @param k: An integer
     * @return: nothing
     */
    public void sortColors2(int[] colors, int k) {

        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        
        for (int i = 0; i < colors.length; i++) {
            int currentCount = map.getOrDefault(colors[i], 0);
            map.put(colors[i], currentCount + 1);
        }
        int index = 0; 
        for (int i = 1; i <= k; i++) {
            int count = map.getOrDefault(i, 0);
            for (int j = 0; j < count; j++) {
                colors[index] = i; 
                index++;
            }
        }

    }
}


```
464 · Sort Integers II

```java
public class Solution {
    /**
     * @param a: an integer array
     * @return: nothing
     */
    public void sortIntegers2(int[] a) {
        // write your code here
        int[] save = new int[a.length];
        mergeSort(a, 0, a.length - 1, save);
    }
    private void mergeSort(int[] a, int start, int end, int[] save) {
        if (start >= end) {
            return;
        }
        mergeSort(a, start, (end + start) / 2, save );
        mergeSort(a, (end + start) / 2 + 1, end, save);
        merge(a, start, end, save);
    }
    public void merge(int[] a, int start, int end, int[] save) {

        int indexStart = start;
        int indexEnd = (end + start) / 2 + 1;
        int index = start;

        while (indexStart <= ((end + start) / 2) && indexEnd <= end) {
            if (a[indexStart] < a[indexEnd]) {
                save[index++] = a[indexStart++];
            } else {
                save[index++] = a[indexEnd++];
            }
        }
        while (indexStart <= (end + start) / 2) {
            save[index++] = a[indexStart++];
        }
        while (indexEnd <= end) {
            save[index++] = a[indexEnd++];
        }  
        for (int i = 0; i <= end; i++) {
            a[i] = save[i];
        }
    } 
}

```

461 · Kth Smallest Numbers in Unsorted Array

```java
public class Solution {
    /**
     * @param k: An integer
     * @param nums: An integer array
     * @return: kth smallest element
     */
    public int kthSmallest(int k, int[] nums) {
        // write your code here
        return quickSelect(nums, 0, nums.length - 1, k - 1);
    }
    private int quickSelect(int[]nums, int start, int end, int k) {
        if (start >= end) {
            return nums[k];
        }
        int left = start;
        int right = end;
        int mid = nums[(start + end) / 2];

        while (left <= right) {
            while (left <= right && nums[left] < mid) {
                left++;
            }
            while (left <= right && nums[right] > mid) {
                right--;
            }
            if (left <= right) {
                swap(nums, left, right);
                left++;
                right--;
            }
        }
        if (k <= right) {
            return quickSelect( nums, start, right, k);
        } else if (k >= left) {
            return quickSelect( nums, left, end, k);
        } else {
            return nums[k];
        }
    }
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}

```

5 · Kth Largest Element

```java
public class Solution {
    /**
     * @param k: An integer
     * @param nums: An array
     * @return: the Kth largest element
     */
    public int kthLargestElement(int k, int[] nums) {
        // write your code here
        return quickSelect(nums, 0, nums.length - 1, nums.length - k);
    }
    private int quickSelect(int[]nums, int start, int end, int k) {
        if (start >= end) {
            return nums[k];
        }
        int left = start;
        int right = end;
        int mid = nums[(start + end) / 2];

        while (left <= right) {
            while (left <= right && nums[left] < mid) {
                left++;
            }
            while (left <= right && nums[right] > mid) {
                right--;
            }
            if (left <= right) {
                swap(nums, left, right);
                left++;
                right--;
            }
        }
        if (k <= right) {
            return quickSelect( nums, start, right, k);
        } else if (k >= left) {
            return quickSelect( nums, left, end, k);
        } else {
            return nums[k];
        }
    }
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}

```

6 · Merge Two Sorted Arrays

```java
class Solution {
    /**
     * @param A and B: sorted integer array A and B.
     * @return: A new sorted integer array
     */
    public int[] mergeSortedArray(int[] A, int[] B) {
        if (A == null || B == null) {
            return null;
        }
        int[] result = new int[A.length + B.length];
        int i = 0;
        int j = 0; 
        int index = 0;
        
        while (i < A.length && j < B.length) {
            if (A[i] < B[j]) {
                result[index++] a= A[i++];
            } else {
                result[index++] = B[j++];
            }
        }
        while (i < A.length) {
            result[index++] = A[i++];
        }
        while (j < B.length) {
            result[index++] = B[j++];
        }
        return result;
    }
}

```

80 · Median

```java
// O(n)
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: An integer denotes the middle number of the array
     */
    public int median(int[] nums) {
        if (nums == null) {
            return -1;
        }
        return quickSelect(nums, 0, nums.length - 1, (nums.length + 1) / 2);  
    }
    private int quickSelect(int[] nums, int left, int right, int k) {
        int start = left;
        int end = right;
        int pivot = nums[(left + right) / 2];

        while (start <= end) {
            while (start <= end && nums[start] < pivot) {
                start++;
            }
            while (start <= end && nums[end] > pivot) {
                end--;
            }
            if (start <= end) {
                swap(nums, start, end);
                start++;
                end--;
            }
        }
        if (left + k - 1 <= end) {
            return quickSelect(nums, left, end, k);
        }
        if (left + k - 1 >= start) {
            return quickSelect(nums, start, right, k - (start - left));
        }
        return nums[end + 1];
    }
    
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}

```
Wrong

```java

public class Solution {
    /**
     * @param k: An integer
     * @param nums: An integer array
     * @return: kth smallest element
     */
    public int kthSmallest(int k, int[] nums) {
        // write your code here
        return quickSelect(nums, 0, nums.length-1, k - 1);
    }
    private int quickSelect(int[] nums, int start, int end, int k) {
        int (start == end) {
            return numss[start];
        }
        int left = start;
        int right = end;
        
        int mid = nums[(right - left) / 2];

        while (left <= right) {
            while (left <= right && nums[left] < mid) {
                left++;
            }
            while (left <= right && nums[right] > mid) {
                right--;
            }
            if (left <= right) {
                int temp = nums[left];
                nums[left] = nums[right];
                nums[right] = temp;
                left++;
                right--;
            }
        }
        if (start < end && right > k) {
            return quickSelect(nums, start, mid, k);
        }
        if (start < end && left < k ) {
            return quickSelect(nums, mid, end, k);
        } else {
            return nums[start];
        }
    }
}

```

585 · Maximum Number in Mountain Sequence
```java
public class Solution {
    /**
     * @param nums: a mountain sequence which increase firstly and then decrease
     * @return: then mountain top
     */
    public int mountainSequence(int[] nums) {
        // write your code here
        if (nums == null) {
            return 0;
        }
        int start = 0;
        int end = nums.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;

            if (nums[mid] > nums[mid + 1]) {
                end = mid;
            } else {
                start = mid;
            }
        }
        return Math.max(nums[start], nums[end]);
    }
}

```
457 · Classical Binary Search

```java

public class Solution {
    /**
     * @param nums: An integer array sorted in ascending order
     * @param target: An integer
     * @return: An integer
     */
    public int findPosition(int[] nums, int target) {
        // write your code here
        if (nums == null) {
            return 0;
        }
        int start = 0;
        int end = nums.length - 1;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            int num = nums[mid];
            if (num == target) {
                return mid;
            } else if (num > target) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }
        return -1;
    }
}
```

14 · First Position of Target

```java
public class Solution {
    /**
     * @param nums: The integer array.
     * @param target: Target to find.
     * @return: The first position of target. Position starts from 0.
     */
    public int binarySearch(int[] nums, int target) {
        // write your code here
        if (nums == null) {
            return 0;
        }
        int start = 0;
        int end = nums.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] == target) {
                end = mid;
            } else if (nums[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (nums[start] == target) {
            return start;
        } 
        if (nums[end] == target) {
            return end;
        }
        return -1;
    }
}

```
196 · Missing Number

```java

public class Solution {
    /**
     * @param nums: An array of integers
     * @return: An integer
     */
    public int findMissing(int[] nums) {
        // write your code here
        int length = nums.length;
        int total = length * (length + 1) / 2;
        int count = 0;
        for (int i = 0; i < length; i++) {
            count = count + nums[i];
        }
        return total - count;
    }
}
```
75 · Find Peak Element
```java

class Solution {
    /**
     * @param A: An integers array.
     * @return: return any of peek positions.
     */
    public int findPeak(int[] A) {

        int start = 1;
        int end = A.length - 2;

        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (A[mid] < A[mid - 1]) {
                end = mid;
            } else if (A[mid] < A[mid + 1]) {
                start = mid;
            } else {
                return mid;
            }
        }
        if (A[start] < A[end]) {
            return end;
        } else {
            return start;
        }
    }
}


       
```

159 · Find Minimum in Rotated Sorted Array
```java
public class Solution {
    /**
     * @param nums: a rotated sorted array
     * @return: the minimum number in the array
     */
    public int findMin(int[] nums) {
        // write your code here
        if (nums == null || nums.length == 0) {
            return -1;
        }
        
        int start = 0, end = nums.length - 1;
        
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] > nums[end]) {
                start = mid;
            } else {
                end = mid;
            }
        }
        
        return Math.min(nums[start], nums[end]);
    }
}
```
17 · Subsets DFS
```java
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
        helper(new ArrayList<Integer>(), nums, 0, results);
        return results;
    }

    private void helper(ArrayList<Integer> subset, int[] nums, int startIndex, List<List<Integer>> results) {

        results.add(new ArrayList<Integer>(subset));
        
        for (int i = startIndex; i < nums.length; i++) {
            subset.add(nums[i]);
            helper(subset, nums, i + 1, results);
            subset.remove(subset.size() - 1);
        }
    }
}

```
17 · Subsets BFS
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
15 · Permutations

```java

public class Solution {
    /**
     * @param nums: A list of integers.
     * @return: A list of permutations.
     *          we will sort your return value in output
     */
    public List<List<Integer>> permute(int[] nums) {
        // write your code here
        List<List<Integer>> result = new ArrayList<>();
        if (nums == null) {
            return result;
        }
        helper(nums, new boolean[], new ArrayList<Integer>(), result);
        return result;
    }
    private void helper(int[] nums, boolean[] used, List<Integer> current, List<List<Integer>> result) {
        if (nums.length == current.size()) {
            result.add(new ArrayList<Integer>(current));
        }
        for (i = 0; i < nums.length; i++) {
            if (used[i]) {
                continue;
            }
            current.add(nums[i]);
            used[i] = true;
            helper(nums, used, current, result);
            used[i] = false;
            current.remove(current.size() - 1);
        }
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
        // write your code here
        List result = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        if (root == null) {
            return result;
        }
        queue.offer(root);
        while (!queue.isEmpty()) {
            ArrayList<Integer> level = new ArrayList<Integer>();
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                TreeNode head = queue.poll();
                level.add(head.val);
                if (head.left != null) {
                    queue.offer(head.left);
                }
                if (head.right != null) {
                    queue.offer(head.right);
                }
            }
            result.add(level);
        }
        return result;
    }
}

```
427 · Generate Parentheses

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

135 · Combination Sum

```java
public class Solution {
    /**
     * @param candidates: A list of integers
     * @param target: An integer
     * @return: A list of lists of integers
     *          we will sort your return value in output
     */
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        // write your code here
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> comb = new ArrayList<>();
        if ( candidates == null) {
            return result;
        }
        Arrays.sort(candidates);
        helperDfs(candidates, 0, target, comb, result);
        return result;
    }
    private void helperDfs(int[] candidates, int index, int target, List<Integer> comb, List<List<Integer>> result) {
        if (target == 0) {
            result.add(new ArrayList<Integer>(comb));
        }
        for (int i = index; i < candidates.length; i++) {
            if (candidates[i] > target) {
                break;
            }
            if (i != 0 && candidates[i] == candidates[i - 1]) {
                continue;
            }
            comb.add(candidates[i]);
            helperDfs(candidates, i, target - candidates[i], comb, result);
            comb.remove(comb.size() - 1);

        }

    }
}

```
153 · Combination Sum II

```java
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> results = new ArrayList<>();
        List<Integer> combination = new ArrayList<Integer>();
        if (candidates == null || candidates.length == 0) {
            return results;
        }
        
        Arrays.sort(candidates);
        helper(candidates, 0, combination, target, results);
        
        return results;
    }
    
    private void helper(int[] candidates, int startIndex, List<Integer> combination, int target, List<List<Integer>> results) {
        
        if (target == 0) {
            results.add(new ArrayList<Integer>(combination));
            return;
        }
        
        for (int i = startIndex; i < candidates.length; i++) {
            if (i != startIndex && candidates[i] == candidates[i - 1]) {
                continue;
            }
            if (target < candidates[i]) {
                break;
            }
            combination.add(candidates[i]);
            helper(candidates, i + 1, combination, target -candidates[i], results);
            combination.remove(combination.size() - 1);
        }
    }
}

```
136 · Palindrome Partitioning
```java
public class Solution {
    /*
     * @param s: A string
     * @return: A list of lists of string
     */
    public List<List<String>> partition(String s) {
        // write your code here
        List<List<String>> result = new ArrayList<>();
        List<String> temp = new ArrayList<String>();

        if (s == null || s.length() == 0) {
            return result;
        }
        helper(s, 0, temp, result);
        return result;
    }
    private void helper(String s, int index, List<String> temp, List<List<String>> result) {
        if (index == s.length()) {
            result.add(new ArrayList<String>(temp));
            return;
        }

         for (int i = index; i < s.length(); i++) {
            String subString = s.substring(index, i + 1);
            if (!isPalindrome(subString)) {
                continue;
            }
            temp.add(subString);
            helper(s, i + 1, temp, result);
            temp.remove(temp.size() - 1);
        }
    }
    private boolean isPalindrome(String s) {
        for (int i = 0, j = s.length() - 1; i < j; i++, j--) {
            if (s.charAt(i) != s.charAt(j)) {
                return false;
            }        
        }
        return true;
    }
}

```
16 · Permutations II

```java

public class Solution {
    /*
     * @param :  A list of integers
     * @return: A list of unique permutations
     */
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        Deque<Integer> path = new ArrayDeque<>(nums.length);
        boolean[] used = new boolean[nums.length];
  
        Arrays.sort(nums);
 
        dfs(nums, used, path, res);
        return res;
    }
        private void dfs(int[] nums, boolean[] used, Deque<Integer> path, List<List<Integer>> res) {

        if (path.size() == nums.length) {
            res.add(new ArrayList<>(path));
            return;
        }

        for (int i = 0; i < nums.length; ++i) {
            
            if ((used[i]) || (i > 0 && nums[i] == nums[i - 1] && !used[i - 1])) {
                continue;
            }
            
            path.addLast(nums[i]);
            used[i] = true;
            dfs(nums, used, path, res);
            used[i] = false;
            path.removeLast();
        }
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
    public List<Integer> preorderTraversal(TreeNode root) {
        Stack<TreeNode> stack = new Stack<TreeNode>();
        List<Integer> preorder = new ArrayList<Integer>();
        
        if (root == null) {
            return preorder;
        }
        
        stack.push(root);
        while (!stack.empty()) {
            TreeNode node = stack.pop();
            preorder.add(node.val);
            if (node.right != null) {
                stack.push(node.right);
            }
            if (node.left != null) {
                stack.push(node.left);
            }
        }
        
        return preorder;
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
        List<Integer> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        List left = inorderTraversal(root.left);
        List right = inorderTraversal(root.right);

        result.addAll(left);
        result.add(root.val);
        result.addAll(right);

        return result;
    }
}

```
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
     * @return: Inorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> inorderTraversal(TreeNode root) {
        Stack<TreeNode> stack = new Stack<TreeNode>();
        ArrayList<Integer> result = new ArrayList<Integer>();
        TreeNode curt = root;
        while (curt != null || !stack.empty()) {
            while (curt != null) {
                stack.add(curt);
                curt = curt.left;
            }
            curt = stack.pop();
            result.add(curt.val);
            curt = curt.right;
        }
        return result;
    }
}

```

86 · Binary Search Tree Iterator
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
 * Example of iterate a tree:
 * BSTIterator iterator = new BSTIterator(root);
 * while (iterator.hasNext()) {
 *    TreeNode node = iterator.next();
 *    do something for node
 * } 
 */
public class BSTIterator {
    private Stack<TreeNode> stack = new Stack<>();
    
    public BSTIterator(TreeNode root) {
        while (root != null) {
            stack.push(root);
            root = root.left;
        }
    }

    public boolean hasNext() {
        return !stack.isEmpty();
    }
    
    public TreeNode next() {
        TreeNode current = stack.peek();
        TreeNode node = current;

        if (node.right == null) {
            node = stack.pop();
            while (!stack.isEmpty() && stack.peek().right == node) {
                node = stack.pop();
            }
        } else {
            node = node.right;
            while (node != null) {
                stack.push(node);
                node = node.left;
            }
        }
        
        return current;
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
public ArrayList<Integer> postorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();

    if (root == null) {
        return result;
    }

    result.addAll(postorderTraversal(root.left));
    result.addAll(postorderTraversal(root.right));
    result.add(root.val);

    return result;   
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
public ArrayList<Integer> postorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    Stack<TreeNode> stack = new Stack<TreeNode>();
    TreeNode prev = null; 
    TreeNode curr = root;

    if (root == null) {
        return result;
    }

    stack.push(root);
    while (!stack.empty()) {
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
```

71 · Binary Tree Zigzag Level Order Traversal
```java
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        if (root == null) {
            return result;
        }
        
        Queue<TreeNode> q = new LinkedList<TreeNode>();
        
        boolean isForward = true;
        q.offer(root);
        while (!q.isEmpty()) {
            int size = q.size();
            List<Integer> subList = new ArrayList<Integer>();
            for (int i = 0; i < size; i++) {
                TreeNode node = q.poll();
                subList.add(node.val);
                if (node.left != null) {
                    q.offer(node.left);
                }
                if (node.right != null) {
                    q.offer(node.right);
                }
            }
            if (!isForward) {
                Collections.reverse(subList);
            }
            result.add(subList);
            isForward = !isForward;
        }
        return result;
    }
}

```


242 · Convert Binary Tree to Linked Lists by Depth
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
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    /**
     * @param root the root of binary tree
     * @return a lists of linked list
     */
    public List<ListNode> binaryTreeToLists(TreeNode root) {
        List<ListNode> result = new ArrayList<ListNode>();
        
        if (root == null)
            return result;
            
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        queue.offer(root);
        
        ListNode dummy = new ListNode(0);
        ListNode lastNode = null;
        while (!queue.isEmpty()) {
            dummy.next = null;
            lastNode = dummy;
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                TreeNode head = queue.poll();
                lastNode.next = new ListNode(head.val);
                lastNode = lastNode.next;

                if (head.left != null)
                    queue.offer(head.left);
                if (head.right != null)
                    queue.offer(head.right);
            }
            result.add(dummy.next);
        }
        
        return result;
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

leetcode 344
Reverse String

```java
class Solution {
    public void reverseString(char[] s) {
        int n = s.length;
        int left = 0;
        int right = n - 1;
        while (left < right) {
            char temp = s[left];
            s[left] = s[right];
            s[right] = temp;
            
            left++;
            right--;
        }
        System.out.println(Arrays.toString(s));
    }
}
```
8 · Rotate Character Array
```java

public class Solution {
    /**
     * @param s: An array of char
     * @param offset: An integer
     * @return: nothing
     */
    public void rotateString(char[] str, int offset) {
        if (str == null || str.length == 0) return;
        offset %= str.length;
        reverse(str, 0, str.length - offset - 1);
        reverse(str, str.length - offset, str.length - 1);
        reverse(str, 0, str.length - 1);
    }
    
    private void reverse(char[] str, int start, int end) {
        while (start < end) {
            char temp = str[start];
            str[start] = str[end];
            str[end] = temp;
            start += 1;
            end -= 1;
        }
    }
}
```
119 · Edit Distance

```java
public class Solution {
    /**
     * @param word1: A string
     * @param word2: A string
     * @return: The minimum number of steps
     */
    public int minDistance(String word1, String word2) {
        int n = word1.length();
        int m = word2.length();

        if (n * m == 0) {
            return n + m;
        }

        int[][] D = new int[n + 1][m + 1];

        for (int i = 0; i < n + 1; i++) {
            D[i][0] = i;
        }
        for (int j = 0; j < m + 1; j++) {
            D[0][j] = j;
        }

        for (int i = 1; i < n + 1; i++) {
            for (int j = 1; j < m + 1; j++) {
                int left = D[i - 1][j] + 1;
                int down = D[i][j - 1] + 1;
                int left_down = D[i - 1][j - 1];
                if (word1.charAt(i - 1) != word2.charAt(j - 1)) {
                    left_down += 1;
                }
                D[i][j] = Math.min(left, Math.min(down, left_down));
            }
        }
        return D[n][m];
    }
}

```
33 · N-Queens

```java
class Solution {
    public List<List<String>> solveNQueens(int n) {
        int[] queens = new int[n];
        Arrays.fill(queens, -1);
        List<List<String>> solutions = new ArrayList<List<String>>();
        solve(solutions, queens, n, 0, 0, 0, 0);
        return solutions;
    }

    public void solve(List<List<String>> solutions, int[] queens, int n, int row, int columns, int diagonals1, int diagonals2) {
        if (row == n) {
            List<String> board = generateBoard(queens, n);
            solutions.add(board);
        } else {
            int availablePositions = ((1 << n) - 1) & (~(columns | diagonals1 | diagonals2));
            while (availablePositions != 0) {
                int position = availablePositions & (-availablePositions);
                availablePositions = availablePositions & (availablePositions - 1);
                int column = Integer.bitCount(position - 1);
                queens[row] = column;
                solve(solutions, queens, n, row + 1, columns | position, (diagonals1 | position) << 1, (diagonals2 | position) >> 1);
                queens[row] = -1;
            }
        }
    }

    public List<String> generateBoard(int[] queens, int n) {
        List<String> board = new ArrayList<String>();
        for (int i = 0; i < n; i++) {
            char[] row = new char[n];
            Arrays.fill(row, '.');
            row[queens[i]] = 'Q';
            board.add(new String(row));
        }
        return board;
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

class Solution {
    public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        queue.offer(root);
        int ans = 0;
        while (!queue.isEmpty()) {
            int size = queue.size();
            while (size > 0) {
                TreeNode node = queue.poll();
                if (node.left != null) {
                    queue.offer(node.left);
                }
                if (node.right != null) {
                    queue.offer(node.right);
                }
                size--;
            }
            ans++;
        }
        return ans;
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
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        List<TreeNode> path_p = getPath(root, p);
        List<TreeNode> path_q = getPath(root, q);
        TreeNode ancestor = null;
        for (int i = 0; i < path_p.size() && i < path_q.size(); ++i) {
            if (path_p.get(i) == path_q.get(i)) {
                ancestor = path_p.get(i);
            } else {
                break;
            }
        }
        return ancestor;
    }

    public List<TreeNode> getPath(TreeNode root, TreeNode target) {
        List<TreeNode> path = new ArrayList<TreeNode>();
        TreeNode node = root;
        while (node != target) {
            path.add(node);
            if (target.val < node.val) {
                node = node.left;
            } else {
                node = node.right;
            }
        }
        path.add(node);
        return path;
    }
}

```
22 · Flatten List


```java

/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * public interface NestedInteger {
 *
 *     // @return true if this NestedInteger holds a single integer,
 *     // rather than a nested list.
 *     public boolean isInteger();
 *
 *     // @return the single integer that this NestedInteger holds,
 *     // if it holds a single integer
 *     // Return null if this NestedInteger holds a nested list
 *     public Integer getInteger();
 *
 *     // @return the nested list that this NestedInteger holds,
 *     // if it holds a nested list
 *     // Return null if this NestedInteger holds a single integer
 *     public List<NestedInteger> getList();
 * }
 */
public class Solution {
    public List<Integer> flatten(List<NestedInteger> nestedList) {

        Stack<Iterator<NestedInteger>> stack = new Stack<>();
        stack.push(nestedList.iterator());

        List<Integer> ans = new ArrayList<>();
        
        while(!stack.isEmpty()){
            Iterator<NestedInteger> i = stack.pop();
            while(i.hasNext()){
                NestedInteger n = i.next();
                if(n.isInteger()){
                    ans.add(n.getInteger());
                }else{
                    stack.push(i);
                    stack.push(n.getList().iterator());
                    break;
                }
            }
        }
        return ans;
    }
}
```

39 · Recover Rotated Sorted Array
```java
public class Solution {

    /**
     * @param nums: An integer array
     * @return: nothing
     */
    public void recoverRotatedSortedArray(List<Integer> nums) {
        // write your code here
        for (int i = 0; i < nums.size() - 1; i++) {
            if (nums.get(i) > nums.get(i + 1)) {

                reverse(nums,0,i);
                reverse(nums,i+1,nums.size()-1);
                reverse(nums,0,nums.size()-1);
                
                return;
            }
        }    
    }
         private void reverse(List<Integer> nums, int start, int end) {
            for (int i = start, j = end; i < j; i++, j--) {
            int temp = nums.get(i);
            nums.set(i, nums.get(j));
            nums.set(j, temp);
        }
    }   
}

```
124. Binary Tree Maximum Path Sum

```java
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
public class Solution {
    int max = Integer.MIN_VALUE;
    
    public int maxPathSum(TreeNode root) {
        helper(root);
        return max;
    }
    
    // helper returns the max branch 
    // plus current node's value
    int helper(TreeNode root) {
        if (root == null) return 0;
        
        int left = Math.max(helper(root.left), 0);
        int right = Math.max(helper(root.right), 0);
        
        max = Math.max(max, root.val + left + right);
        
        return root.val + Math.max(left, right);
    }
}

```

114 · Unique Paths


```java
public class Solution {
    /**
     * @param m: positive integer (1 <= m <= 100)
     * @param n: positive integer (1 <= n <= 100)
     * @return: An integer
     */
    public int uniquePaths(int m, int n) {
        // write your code here
        int [][] dp = new int [m][n];
        dp[0][0] = 1;
        for (i = 0; i < n; i++) {
            for (j = ; j < n; j++) {
                if (i == 0 || j == 0) {
                    dp[i][j] = 1;
                } else {
                    dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
                }
            }
        }
        return dp[m - 1] [n - 1];
    }
}

```


110 · Minimum Path Sum

```java
public class Solution {
    /**
     * @param grid: a list of lists of integers
     * @return: An integer, minimizes the sum of all numbers along its path
     */
    public int minPathSum(int[][] grid) {
        // write your code here
        if (grid == null) {
            return 0;
        }
        int m = grid.length;
        int n = grid[0].length;
        int[][] f = new int[m][n];

        f[0][0]= grid[0][0];
        for (int i = 1; i < m; i++) {
            f[i][0] = f[i - 1][0] + grid[i][0];

        }
        for (int j = 1; j < n; j++) {
            f[0][j] = f[0][j - 1] + grid[0][j];
        }
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                f[i][j] = Math.min(f[i - 1][j], f[i][j - 1]) + grid[i][j];
            }
        }
        return f[m - 1][n - 1];
    }
}

```
547 · Intersection of Two Arrays
```java
public class Solution {
    /**
     * @param nums1: an integer array
     * @param nums2: an integer array
     * @return: an integer array
     *          we will sort your return value in output
     */
    public int[] intersection(int[] nums1, int[] nums2) {
        // write your code here

        Arrays.sort(nums1);
        Arrays.sort(nums2);

        int length1 = nums1.length,;
        int length2 = nums2.length;

        int[] intersection = new int[length1 + length2];

        int index = 0;
        int index1 = 0;
        int index2 = 0;

        while (index1 < length1 && index2 < length2) {
            int num1 = nums1[index1], num2 = nums2[index2];
            if (num1 == num2) {
                if (index == 0 || num1 != intersection[index - 1]) {
                    intersection[index++] = num1;
                }
                index1++;
                index2++;
            } else if (num1 < num2) {
                index1++;
            } else {
                index2++;
            }
        }
        return Arrays.copyOfRange(intersection, 0, index);
    }
}



```
85 · Insert Node in a Binary Search Tree
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
    /*
     * @param root: The root of the binary search tree.
     * @param node: insert this node into the binary search tree
     * @return: The root of the new binary search tree.
     */
    public TreeNode insertNode(TreeNode root, TreeNode node) {
        // write your code here

        if (root == null) {
            return node;
        }
        TreeNode insert = root;
        while (insert != null) {
            if (node.val < insert.val) {
                if (insert.left == null) {
                    insert.left = node;
                    break;
                } else {
                    insert = insert.left;
                }
            } else {
                if (insert.right == null) {
                    insert.right = node;
                    break;
                } else {
                    insert = insert.right;
                }
            }
        }
        return root;
    }
}

```
174 · Remove Nth Node From End of List
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
     * @param head: The first node of linked list.
     * @param n: An integer
     * @return: The head of linked list.
     */
    public ListNode removeNthFromEnd(ListNode head, int n) {
        // write your code here

        ListNode dummy = new ListNode(0);
        dummy.next = head;
        int length = getLength(head);
        ListNode cur = dummy;
        for (int i = 1; i < length - n + 1; ++i) {
            cur = cur.next;
        }
        cur.next = cur.next.next;
        ListNode ans = dummy.next;
        return ans;
    }

    public int getLength(ListNode head) {
        int length = 0;
        while (head != null) {
            ++length;
            head = head.next;
        }
        return length;
    }
}

```
152. Maximum Product Subarray
```java
public class Solution {
    public int maxProduct(int[] A) {
        if (A == null || A.length == 0) {
            return 0;
        }
        int max = A[0], min = A[0], result = A[0];
        for (int i = 1; i < A.length; i++) {
            int temp = max;
            max = Math.max(Math.max(max * A[i], min * A[i]), A[i]);
            min = Math.min(Math.min(temp * A[i], min * A[i]), A[i]);
            if (max > result) {
                result = max;
            }
        }
        return result;
    }
}



```
116 · Jump Game

```java
public class Solution {
    /*
     * @param A: A list of integers
     * @return: A boolean
     */
    public boolean canJump(int[] A) {
        // write your code here
        if(A == null || A.length == 0){
            return false;
        }
        if(A.length == 1){
            return true;
        }
        
        int gap = 0;
        for(int i = A.length - 2; i >= 0; i--){
            if(A[i] - gap <= 0){
                gap++;
            }else{
                gap = 0;
            }
        }
        return gap == 0;
    }
}

```
116 · Jump Game
```java
public class Solution {
    /*
     * @param A: A list of integers
     * @return: A boolean
     */
    public boolean canJump(int[] A) {
        // write your code here
        if(A == null || A.length == 0){
            return false;
        }
        if(A.length == 1){
            return true;
        }
        
        int gap = 0;
        for(int i = A.length - 2; i >= 0; i--){
            if(A[i] - gap <= 0){
                gap++;
            }else{
                gap = 0;
            }
        }
        return gap == 0;
    }
}

```
116 · Jump Game
```java
public class Solution {
    /*
     * @param A: A list of integers
     * @return: A boolean
     */
    public boolean canJump(int[] A) {
       if (A.length == 0) {
           return false;
       }

       boolean[] dp = new boolean[A.length];
       dp[0] = true;

       for (int i = 1; i < A.length; i++) {
           for (int j = 0; j < i; j++) {
               if (dp[j] && A[j] + j >= i) {
                   dp[i] = true;
                   break;
               }
           }
       }
       return dp[A.length - 1];
    }
}

```
116 · Jump Game

```java
public class Solution {
    /*
     * @param A: A list of integers
     * @return: A boolean
     */
    public boolean canJump(int[] A) {
       int n = A.length;
       int rightmost = 0;
       for (int i = 0; i < n; i++) {
           if (i <= rightmost) {
               rightmost = Math.max(rightmost, i + A[i]);
               if (rightmost >= n - 1) {
                   return true;
               }
           }
       }
       return false;
    }
}

```
117 · Jump Game II

```java
public class Solution {
    public int jump(int[] a) {
        int length = a.length;
        int end = 0;
        int maxPosition = 0; 
        int steps = 0;
        for (int i = 0; i < length - 1; i++) {
            maxPosition = Math.max(maxPosition, i + a[i]);
            if (i == end) {
                end = maxPosition;
                steps++;
            }
        }
        return steps;
    }
}

```

117 · Jump Game II

```java

public class Solution {
    /**
     * @param A: A list of integers
     * @return: An integer
     */
    public int jump(int[] A) {
        // write your code here
        if (A == null || A.length == 0) {
            return 0;
        }
        
        int n = A.length;
        int[] dp = new int[n];
        
        for (int i = 1; i < n; i++) {
            dp[i] = i;
            for (int j = 0; j <= i; j++) {
                if (A[j] + j >= i) {
                    dp[i] = Math.min(dp[j] + 1, dp[i]);
                }
            }
        }
        return dp[n-1];
    }
}
```

107 · Word Break  DP

```java
public class Solution {
    /*
     * @param s: A string
     * @param dict: A dictionary of words dict
     * @return: A boolean
     */
    public boolean wordBreak(String s, Set<String> dict) {
        if (s == null) {
            return true;
        }
        
        int maxLength = 0;
        for (String word : dict) {
            maxLength = Math.max(maxLength, word.length());
        }
      
        int n = s.length();
        boolean[] dp = new boolean[n + 1];
        dp[0] = true;
        
        for (int i = 1; i <= n; i++) {
            for (int l = 1; l <= maxLength; l++) {
                if (i < l) {
                    break;
                }
                if (!dp[i - l]) {
                    continue;
                }
                String word = s.substring(i - l, i);
                if (dict.contains(word)) {
                    dp[i] = true;
                    break;
                }
            }
        }
        
        return dp[n];
    }
}

```
DFS

```java
public class Solution {
    public boolean wordBreak(String s, Set<String> dict) {
        return dfs(s, dict, 0); 
    }
    
    public boolean dfs(String s, Set<String> dict, int now) {

        if (now == s.length()) {
            return true;
        }
        
        for (int len = 1; now + len <= s.length(); len++) {
            if (dict.contains(s.substring(now, now + len)) && dfs(s, dict, now + len)) {
                return true;
            }
        }
        return false;
    }
}

```
N-Queens 2

```java
public class Solution {
    /**
     * @param n: The number of queens.
     * @return: The total number of distinct solutions.
     */
    int result = 0;
    int n;
    Set<Integer> sum = new HashSet<Integer>();
    Set<Integer> diff = new HashSet<Integer>();
    Set<Integer> collin = new HashSet<Integer>();

    private void search(int level) {
        if (level == n) {
            result++;
            return;
        }

        for (int i = 0; i < n; i++) {
            if (!collin.contains(i) && !diff.contains(level - i) && !sum.contains(level + i)) {
                collin.add(i);
                diff.add(level - i);
                sum.add(level + i);
                search(level + 1);
                collin.remove(i);
                diff.remove(level - i);
                sum.remove(level + i);
            }
        }
    }


    public int totalNQueens(int nn) {
        n = nn;
        
        if (n <= 0) {
            return 0;
        }
        search(0);
        return result;
    }
}
```


N-Queens

```java

class Solution {
    /**
     * Get all distinct N-Queen solutions
     * @param n: The number of queens
     * @return: All distinct solutions
     * For example, A string '...Q' shows a queen on forth position
     */
    public List<List<String>> solveNQueens(int n) {

        List<List<String>> results = new ArrayList<>();
        if (n <= 0) {
            return results;
        }
        
        search(results, new ArrayList<Integer>(), n);
        return results;
    }
    
    private void search(List<List<String>> results, List<Integer> cols, int n) {
        if (cols.size() == n) {
            results.add(Draw(cols));
            return;
        }
        for (int colIndex = 0; colIndex < n; colIndex++) {
            if (!isValid(cols, colIndex)) {
                continue;
            }
            cols.add(colIndex);
            search(results, cols, n);
            cols.remove(cols.size() - 1);
        }
    }
    
    private boolean isValid(List<Integer> cols, int col) {
        int row = cols.size();
        for (int rowIndex = 0; rowIndex < cols.size(); rowIndex++) {
            if (cols.get(rowIndex) == col) {
                return false;
            }
            if (row + col == rowIndex + cols.get(rowIndex)) {
                return false;
            }
            if (row - col == rowIndex - cols.get(rowIndex)) {
                return false;
            }
        }
        return true;
    }
    private List<String> Draw(List<Integer> cols) {
        List<String> result = new ArrayList<>();
        for (int i = 0; i < cols.size(); i++) {
            StringBuilder sb = new StringBuilder();
            for (int j = 0; j < cols.size(); j++) {
                sb.append(j == cols.get(i) ? 'Q' : '.');
            }
            result.add(sb.toString());
        }
        return result;
    }
}
```
104 · Merge K Sorted Lists
```java

// version 1: Divide & Conquer
/**
 * Definition for ListNode.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) {
 *         this.val = val;
 *         this.next = null;
 *     }
 * }
 */ 
public class Solution {
    /**
     * @param lists: a list of ListNode
     * @return: The head of one sorted list.
     */
    public ListNode mergeKLists(List<ListNode> lists) {
        if (lists.size() == 0) {
            return null;
        }
        return mergeHelper(lists, 0, lists.size() - 1);
    }
    
    private ListNode mergeHelper(List<ListNode> lists, int start, int end) {
        if (start == end) {
            return lists.get(start);
        }
        
        int mid = start + (end - start) / 2;
        ListNode left = mergeHelper(lists, start, mid);
        ListNode right = mergeHelper(lists, mid + 1, end);
        return mergeTwoLists(left, right);
    }
    
    private ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;
        while (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
                tail.next = list1;
                tail = list1;
                list1 = list1.next;
            } else {
                tail.next = list2;
                tail = list2;
                list2 = list2.next;
            }
        }
        if (list1 != null) {
            tail.next = list1;
        } else {
            tail.next = list2;
        }
        
        return dummy.next;
    }
}

```
56 · Two Sum


```java
public class Solution {
    /**
     * @param numbers: An array of Integer
     * @param target: target = numbers[index1] + numbers[index2]
     * @return: [index1, index2] (index1 < index2)
     */
    public int[] twoSum(int[] numbers, int target) {
        // write your code here
        HashMap<Integer,Integer> map = new HashMap<>();
         

        for (int i = 0; i < numbers.length; i++) {
            if (map.get(numbers[i]) != null) {
                int[] result = {map.get(numbers[i]), i};
                return result;
            }
            map.put(target - numbers[i], i);
        }
        int[] result = {};
        return result;
    }
}


```
57 · 3Sum


```java
public class Solution {
    /**
    * @param numbers : Give an array numbers of n integer
    * @return : Find all unique triplets in the array which gives the sum of zero.
    */
    public List<List<Integer>> threeSum(int[] numbers) {
        Arrays.sort(numbers);
        
        List<List<Integer>> results = new ArrayList();
        for (int i = 0; i < numbers.length; i++) {
            if (i != 0 && numbers[i] == numbers[i - 1]) {
               continue;
            }
            findTwoSum(numbers, i, results);
        }
        
        return results;
    }
    
    private void findTwoSum(int[] nums, int index, List<List<Integer>> results) {
        int left = index + 1, right = nums.length - 1;
        int target = -nums[index];
        
        while (left < right) {
            int twoSum = nums[left] + nums[right];
            if (twoSum < target) {
                left++;
            } else if (twoSum > target) {
                right--;
            } else {
                List<Integer> triple = new ArrayList();
                triple.add(nums[index]);
                triple.add(nums[left]);
                triple.add(nums[right]);
                results.add(triple);
                left++;
                right--;
                while (left < right && nums[left] == nums[left - 1]) {
                    left++;
                }
            }
        }
    }
}

```

58 · 4Sum

```java

public class Solution {
    /**
     * @param numbers: Give an array
     * @param target: An integer
     * @return: Find all unique quadruplets in the array which gives the sum of zero
     */
    public List<List<Integer>> fourSum(int[] numbers, int target) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(numbers);
        dfs(numbers, new ArrayList<Integer>(), target, result, 0);
        return result;
    }
    
    private void dfs(int[] numbers, List<Integer> list, int target, List<List<Integer>> result, int index) {
        if (list.size() == 4) {
            if (target == 0) {
                result.add(new ArrayList<Integer>(list));
            }
            return;
        }
        for (int i = index; i < numbers.length; i++) {
            if (i != index && numbers[i] == numbers[i-1]) {
                continue;
            }
            list.add(numbers[i]);
            dfs(numbers, list, target-numbers[i], result, i+1);
            list.remove(list.size() - 1);
        }
    }
}
```

80 · Median

```java
public class Solution {
    /**
     * @param nums: A list of integers.
     * @return: An integer denotes the middle number of the array.
     */
    public int median(int[] nums) {

        return helper(nums, 0, nums.length - 1, (nums.length + 1)/2);

    }
    private int helper(int[] nums, int start, int end, int size) {

        int mid = (start + end) / 2;
        int pivot = nums[mid];

        int i = start - 1;
        int j = end + 1;
        
        for (int k = start; k < j; k++) {
            if (nums[k] < pivot) {
                i++;
                int tmp = nums[i];
                nums[i] = nums[k];
                nums[k] = tmp;
            } else if (nums[k] > pivot) {
                j--;
                int tmp = nums[j];
                nums[j] = nums[k];
                nums[k] = tmp;
                k--;
            }
        }
        if (i - start + 1 >= size) {
            return sub(nums, start, i, size);
        } else if (j - start >= size) {
            return nums[j-1];
        } else {
            return sub(nums, j, end, size - (j - start));
        }
    }
}

```

65 · Median of two Sorted Arrays

```java

public class Solution {
    /*
     * @param A: An integer array
     * @param B: An integer array
     * @return: a double whose format is *.5 or *.0
     */
    public double findMedianSortedArrays(int[] A, int[] B) {
        int m = A.length;
        int n = B.length;
        
        int p1 = 0;
        int p2 = 0;

        int left = -1;
        int right = -1;

        for (int i = 0; i < (n + m) / 2 + 1; i++) {
            left = right;
            
            if (p1 >= A.length || p2 <B.length && A[p1] > B[p2]) {
                right = B[p2++];
            }
            else {
                right = A[p1++];
            }
        } 
        return (m + n) % 2 == 1 ?  right : (left + right) / 2.0;
    }
}
```

900 · Closest Binary Search Tree Value

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

class Solution {
    public int closestValue(TreeNode root, double target) {

        LinkedList<TreeNode> stack = new LinkedList();
        long pred = Long.MIN_VALUE;

        while (!stack.isEmpty() || root != null) {
            while (root != null) {
                stack.add(root);
                root = root.left;
            }
             
            root = stack.removeLast();

            if (pred <= target && target < root.val)
                return Math.abs(pred - target) < Math.abs(root.val - target) ? (int)pred : root.val;

            pred = root.val;
            root = root.right;
        }
        return (int)pred;
    }
}
```

689 · Two Sum IV - Input is a BST
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
    /*
     * @param : the root of tree
     * @param : the target sum
     * @return: two numbers from tree which sum is n
     */
    public int[] twoSum(TreeNode root,  ) {
        // write your code here
        if (root == null) {
            return null;
        }
        Set<Integer> set = new HashSet<Integer>();
        Queue<TreeNode> queue = new ArrayDeque<TreeNode>();
        queue.offer(root);

        while (!queue.isEmpty()) {

            TreeNode node = queue.poll();

            if (set.contains(n - node.val)) {
                return new int[]{node.val, n - node.val};
            }

            set.add(node.val);
            if (node.left != null) {
                queue.offer(node.left);
            }
            if (node.right != null) {
                queue.offer(node.right);
            }
        }
        return null;
    }
}

```

362 · Sliding Window Maximum

```java
public class Solution {
    int[] a;
    /**
     * @param nums: A list of integers.
     * @return: The maximum number inside the window at each moving.
     */
    private void inQueue(Deque<Integer> deque, int pos) {
        while (!deque.isEmpty() && a[deque.peekLast()] <= a[pos]) {
            deque.pollLast();
        }
        deque.offer(pos);
    }
    
    private void outQueue(Deque<Integer> deque, int pos) {
        if (deque.peekFirst() == pos) {
            deque.pollFirst();
        }
    }
    
    public ArrayList<Integer> maxSlidingWindow(int[] nums, int k) {
        a = nums;

        ArrayList<Integer> result = new ArrayList<Integer>();
        Deque<Integer> deque = new ArrayDeque<Integer>();
        
        if (nums.length == 0) {
            return result;
        }
        for (int i = 0; i < k - 1; i++) {
            inQueue(deque, i);
        }
        
        for(int i = k - 1; i < nums.length; i++) {
            inQueue(deque, i);
            result.add(a[deque.peekFirst()]);
            outQueue(deque, i - k + 1);
        }
        return result;

    }
}


```

423 · Valid Parentheses

```java

public class Solution {
    /**
     * @param s A string
     * @return whether the string is a valid parentheses
     */
    public boolean isValidParentheses(String s) {
        // Write your code here

        Map<Character, Character> map = new HashMap<>();
        map.put(')', '(');
        map.put('}', '{');
        map.put(']', '[');
        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < s.length(); i++) {

            char symbol = s.charAt(i);
            
            if (map.containsKey(symbol)) {
                if (stack.isEmpty() || stack.pop() != map.get(symbol)) {
                    return false;
                }
            } else {
                stack.push(symbol);
            }
        }
        return stack.isEmpty();
    }
}

```
76 · Longest Increasing Subsequence
```java
public class Solution {
    /**
     * @param nums: The integer array
     * @return: The length of LIS (longest increasing subsequence)
     */
    public int longestIncreasingSubsequence(int[] nums) {
       
        if (nums.length == 0) {
            return 0;
        }
        int[] dp = new int[nums.length];
        dp[0] = 1;
        int maxresult = 1;

        for (int i = 1; i < nums.length; i++) {
            dp[i] = 1;
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxresult = Math.max(maxresult, dp[i]);
        }
        return maxresult;
    }
}


```

662 · Guess Number Higher or Lower

```java

/* The guess API is defined in the parent class GuessGame.
   @param num, your guess
   @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
      int guess(int num); */

public class Solution extends GuessGame {
    /**
     * @param n an integer
     * @return the number you guess
     */
    public int guessNumber(int n) {
        // Write your code here
        int i = 1, r = n;
        while (i <= r) {
            int mid = i + (r - i) / 2;
            int result = guess(mid);
            if (result == 0) {
                return mid;
            }
            
            if (result == -1) {
                r = mid - 1;
            } else {
                i = mid + 1;
            }
        }
        return -1;
    }
}

```
74 · First Bad Version

```java

/**
 * public class GitRepo {
 *     public static boolean isBadVersion(int k);
 * }
 * you can use GitRepo.isBadVersion(k) to judge whether 
 * the kth code version is bad or not.
*/
class Solution {
    /**
     * @param n: An integers.
     * @return: An integer which is the first bad version.
     */
    public int findFirstBadVersion(int n) {
        int start = 1;
        int end = n;
        
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (SVNRepo.isBadVersion(mid)) {
                end = mid;
            } else {
                start = mid;
            }
        }
            
        if (SVNRepo.isBadVersion(start)) {
            return start;
        }
        return end;
    }
}

```
457 · Classical Binary Search
```java

public class Solution {
    /**
     * @param A an integer array sorted in ascending order
     * @param target an integer
     * @return an integer
     */
    public int findPosition(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return -1;
        }
        
        int start = 0, end = nums.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        
        if (nums[start] == target) {
            return start;
        }
        if (nums[end] == target) {
            return end;
        }
        return -1;
    }
}

```
459 · Closest Number in Sorted Array

```java

public class Solution {
    /**
     * @param A an integer array sorted in ascending order
     * @param target an integer
     * @return an integer
     */
    public int closestNumber(int[] A, int target) {
        if (A == null || A.length == 0) {
            return -1;
        }
        
        int index = firstIndex(A, target);
        if (index == 0) {
            return 0;
        }
        if (index == A.length) {
            return A.length - 1;
        }

        if (target - A[index - 1] < A[index] - target) {
            return index - 1;
        }
        return index;
    }
    
    private int firstIndex(int[] A, int target) {
        int start = 0, end = A.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (A[mid] < target) {
                start = mid;
            } else if (A[mid] > target) {
                end = mid;
            } else {
                end = mid;
            }
        }
        
        if (A[start] >= target) {
            return start;
        }
        if (A[end] >= target) {
            return end;
        }
        return A.length;
    }
}

```
458 · Last Position of Target
```java

public class Solution {
    /*
     * @param nums: An integer array sorted in ascending order
     * @param target: An integer
     * @return: An integer
     */
    public int lastPosition(int[] nums, int target) {
        // write your code here
        if (nums == null || nums.length == 0) {
            return -1;
        }
        int start = 0;
        int end = nums.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] == target) {
                start = mid;
            } else if (nums[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (nums[end] == target) {
            return end;
        } else if (nums[start] == target) {
            return start;
        } else {
            return -1;
        }
    }
}

```
61 · Search for a Range
```java

public class Solution {
    /**
     * @param A: an integer sorted array
     * @param target: an integer to be inserted
     * @return: a list of length 2, [index1, index2]
     */

    public static int findLastTargetNum(int[] A, int target, int n){
        int left = 0;
        int right = n - 1;
        while (left + 1 < right){
            int mid = left + (right - left) / 2;
            if (A[mid] <= target){
                left = mid;
            }
            else{
                right = mid;
            }
        }
        if (right >= 0 && A[right] == target){
            return right;
        }
        if (left < n && A[left] == target){
            return left;
        }
        return -1;
    }
    
    public int[] searchRange(int[] A, int target) {
        int n = A.length;
        int[] interval = {-1, -1};
        interval[0] = findFirstTargetNum(A, target, n);
        interval[1] = findLastTargetNum(A, target, n);
        return interval;
    }
}




public class Solution {
    /**
     * @param A: an integer sorted array
     * @param target: an integer to be inserted
     * @return: a list of length 2, [index1, index2]
     */

    public static int findFirstTargetNum(int[] A, int target, int n){
        int left = 0, right = n - 1;
        while (left + 1 < right){
            int mid = left + (right - left) / 2;
            if (A[mid] < target){
                left = mid;
            }
            else{
                right = mid;
            }
        }
        if (left < n && A[left] == target){
            return left;
        }
        if (right >= 0 && A[right] == target){
            return right;
        }
        return -1;
    }
}

```

28 · Search a 2D Matrix

```java

public class Solution {
    /**
     * @param matrix: matrix, a list of lists of integers
     * @param target: An integer
     * @return: a boolean, indicate whether matrix contains target
     */
    public boolean searchMatrix(int[][] matrix, int target) {
        // write your code here
        int n = matrix.length;
        int m = matrix[0].length;
        int start = 0;
        int end = n * m - 1;

        while (start + 1 < end) {
            int mid = start + ( end - start) / 2;

            if (get(matrix, mid) < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (get (matrix, start) == target) {
            return true;
        }
        if (get (matrix, end) == target) {
            return true;
        } else {
            return false;
        }
    }
    private int get (int[][] matrix, int index) {
        int x = index / matrix[0].length;
        int y = index % matrix[0].length;
        return matrix[x][y];
    }
}
```

38 · Search a 2D Matrix II
```java

public class Solution {
    /**
     * @param matrix: A list of lists of integers
     * @param: A number you want to search in the matrix
     * @return: An integer indicate the occurrence of target in the given matrix
     */
    public int searchMatrix(int[][] matrix, int target) {
        // write your code here
        int r = matrix.length - 1;
        int c = 0;
        int result = 0;
        while (r >= 0 && c < matrix[0].length) {
            if (target == matrix[r][c]) {
                result++;
                r--;
                c++;
                continue;
            }
            if (target < matrix[r][c]) {
                r--;
            } else {
                c++;
            }
        }
        return result;
    }
}

```

61 · Search for a Range
```java
public class Solution {
    /**
     * @param A: an integer sorted array
     * @param target: an integer to be inserted
     * @return: a list of length 2, [index1, index2]
     */

    public static int findFirstTargetNum(int[] A, int target, int n){
        int left = 0;
        int right = n - 1;
        while (left + 1 < right){
            int mid = left + (right - left) / 2;
            if (A[mid] < target){
                left = mid;
            }
            else{
                right = mid;
            }
        }
        if (left < n && A[left] == target){
            return left;
        }
        if (right >= 0 && A[right] == target){
            return right;
        }
        return -1;
    }
}

```
458 · Last Position of Target

```java
public class Solution {
    /*
     * @param nums: An integer array sorted in ascending order
     * @param target: An integer
     * @return: An integer
     */
    public int lastPosition(int[] nums, int target) {
        // write your code here
        if (nums == null || nums.length == 0) {
            return -1;
        }
        int start = 0;
        int end = nums.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] == target) {
                start = mid;
            } else if (nums[mid] < target) {
                start = mid;
            } else {
                end = mid;
            }
        }
        if (nums[end] == target) {
            return end;
        } else if (nums[start] == target) {
            return start;
        } else {
            return -1;
        }
    }
}

```

459 · Closest Number in Sorted Array
```java
public class Solution {
    /**
     * @param A an integer array sorted in ascending order
     * @param target an integer
     * @return an integer
     */
    public int closestNumber(int[] A, int target) {
        if (A == null || A.length == 0) {
            return -1;
        }
        
        int index = firstIndex(A, target);
        if (index == 0) {
            return 0;
        }
        if (index == A.length) {
            return A.length - 1;
        }

        if (target - A[index - 1] < A[index] - target) {
            return index - 1;
        }
        return index;
    }
    
    private int firstIndex(int[] A, int target) {
        int start = 0, end = A.length - 1;
        while (start + 1 < end) {
            int mid = start + (end - start) / 2;
            if (A[mid] < target) {
                start = mid;
            } else if (A[mid] > target) {
                end = mid;
            } else {
                end = mid;
            }
        }
        
        if (A[start] >= target) {
            return start;
        }
        if (A[end] >= target) {
            return end;
        }
        return A.length;
    }
}

```


```java


```