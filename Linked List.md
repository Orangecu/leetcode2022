Linked List

LintCode 112
Remove Duplicates from Sorted List
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
        if (head == null ) {
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

LintCode
35 
Reverse Linked List

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
        ListNode furt = null;
        ListNode prev = null;
        while (current != null) {
            furt = current.next;
            current.next = prev;
            prev = current;
            current = furt;
        }
        return prev;
    }
}

```

Lintcode
1292 ·
Odd Even Linked List

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
link 96
 Partition List

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
        if ( head == null || head.next == null) {
            return head;
        }
        ListNode dummy1 = new ListNode(0);
        ListNode dummy2 = new ListNode(0);
        ListNode c1 = dummy1;
        ListNode c2 = dummy2;
        ListNode current = head;

        while (current != null) {
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

lintcode 
228
 Middle of Linked List

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
lint
 99
 Reorder List

 ```java

public class Solution {
    private ListNode reverse(ListNode head) {
        ListNode newHead = null;
        while (head != null) {
            ListNode temp = head.next;
            head.next = newHead;
            newHead = head;
            head = temp;
        }
        return newHead;
    }

    private void merge(ListNode head1, ListNode head2) {
        int index = 0;
        ListNode dummy = new ListNode(0);
        while (head1 != null && head2 != null) {
            if (index % 2 == 0) {
                dummy.next = head1;
                head1 = head1.next;
            } else {
                dummy.next = head2;
                head2 = head2.next;
            }
            dummy = dummy.next;
            index ++;
        }
        if (head1 != null) {
            dummy.next = head1;
        } else {
            dummy.next = head2;
        }
    }

    private ListNode findMiddle(ListNode head) {
        ListNode slow = head, fast = head.next;
        while (fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;
        }
        return slow;
    }

    public void reorderList(ListNode head) {
        if (head == null || head.next == null) {
            return;
        }

        ListNode mid = findMiddle(head);
        ListNode tail = reverse(mid.next);
        mid.next = null;

        merge(head, tail);
    }
}
 ```

 lint 
 165 
 Merge Two Sorted Lists

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
     * @param l1: ListNode l1 is the head of the linked list
     * @param l2: ListNode l2 is the head of the linked list
     * @return: ListNode head of linked list
     */
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        // write your code here]
        if (l1 == null) {
            return l2;
        }
        if (l2 == null) {
            return l1;
        }
        ListNode head, current;
        if ( l1.val < l2.val) {
            head = l1;
            l1 = l1.next;
        } else {
            head = l2;
            l2 = l2.next;
        }
        current = head;
        while (l1 != null && l2 != null ) {
            if (l1.val < l2.val) {
                current.next = l1;
                l1 = l1.next;
            } else {
                current.next = l2;
                l2 = l2.next;
            }
            current = current.next;
        }
        if (l1 != null) {
            current.next = l1;
        }
        if (l2 != null) {
            current.next = l2;
        }
        return head;
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
        ListNode prev1;
        ListNode prev2;
        prev1 = dummy;
        prev2 = dummy;

        while (prev1.next != null && prev1.next.val != v1) {
            prev1 = prev1.next;
        }
        while (prev2.next != null && prev2.next.val != v2) {
            prev2 = prev2.next;
        }
        if (prev1.next == null || prev2.next == null) return head;
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

36 · Reverse Linked List II

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
     * @param head: ListNode head is the head of the linked list 
     * @param m: An integer
     * @param n: An integer
     * @return: The head of the reversed ListNode
     */
    public ListNode reverseBetween(ListNode head, int m, int n) {
        // write your code here
        if (m >= n || head == null) {
            return head;
        }
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        head = dummy;

        for (int i = 1; i < m; i++) {
            head = head.next;
        }
        ListNode nmprev= head;
        ListNode nm = nmprev.next;
        ListNode nn = nm;
        for (int i = 0; i < n - m; i++) {
            nn = nn.next;
        }
        ListNode nnplus = nn.next;
        reverse(head, head.next, n - m + 1);
        nm.next = nnplus;
        nmprev.next = nn;
        return dummy.next;
    }
    private void reverse(ListNode prev, ListNode currentt, int k) {
        for (int i = 0; i < k; i++) {
            ListNode current = currentt.next;
            currentt.next = prev;
            prev = currentt;
            currentt = current;            
        }
    }
}
```
380 · Intersection of Two Linked Lists
```java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) {
            return null;
        }
        
        ListNode node = headA;

        while (node.next != null) {
            node = node.next;
        }
        
        node.next = headB;
        ListNode result = findCycleNode(headA);
        node.next = null;
        return result;
    }
    
    private ListNode findCycleNode(ListNode head) {
        ListNode fast, slow;
        fast = head;
        slow = head;
        
        do {
            if (fast == null || fast.next == null) {
                return null;
            }
            fast = fast.next.next;
            slow = slow.next;
        } while (fast != slow);
        
        ListNode result = head;
        while (result != fast) {
            result = result.next;
            fast = fast.next;
        }
        
        return result;
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
170 · Rotate List

```java
class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null) {
            return null;
        }
        
        int length = getLength(head);
        k = k % length;
        
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        head = dummy;
        
        ListNode tail = dummy;
        for (int i = 0; i < k; i++) {
            head = head.next;
        }
        
        while (head.next != null) {
            head = head.next;
            tail = tail.next;
        }
        
        head.next = dummy.next;
        dummy.next = tail.next;
        tail.next = null;
        
        return dummy.next;
    }
    
    private int getLength(ListNode head) {
        int length = 0;
        while (head != null) {
            length++;
            head = head.next;
        }
        return length;
    }
}
```
