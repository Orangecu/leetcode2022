
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
463 · Sort Integers
```java
public class Solution {
    /*
     * @param A: an integer array
     * @return: 
     */
    public void sortIntegers(int[] A) {
        // write your code here
        while (true) {
            boolean exchange = false;
            for (int i = 0; i < A.length - 1; i++) {
                if (A[i] > A[i + 1]) {
                    int tmp = A[i];
                    A[i] = A[i + 1];
                    A[i + 1] = tmp;
                    exchange = true;
                }
            }
            if (!exchange) {
                break;
            }
        }
    }
}
// bubble sort
```
```java
public class Solution {
    /*
     * @param A: an integer array
     * @return: 
     */
    public void sortIntegers(int[] A) {
        // write your code here
        for (int i = 0; i < A.length; i++) {
            int minIdx = i;
            for (int j = i; j < A.length; j++) {
                if (A[j] < A[minIdx]) {
                    minIdx = j;
                }
            }
            int tmp = A[i];
            A[i] = A[minIdx];
            A[minIdx] = tmp;
        }
    }
}
// select sort
```
```java
public class Solution {
    /*
     * @param A: an integer array
     * @return: 
     */
    public void sortIntegers(int[] A) {
        // write your code here
        for (int i = 0; i < A.length; i++) {
            int newVal = A[i];
            int j = i - 1;

            while (j >= 0 && A[j] > newVal) {
                A[j + 1] = A[j];
                j--;
            }
            A[j + 1] = newVal;
        }
    }
}
// insert sort
```
1272 · Kth Smallest Element in a Sorted Matrix
```java
class Solution {
    public int kthSmallest(int[][] matrix, int k) {
        PriorityQueue<int[]> queue = new PriorityQueue<int[]>(new Comparator<int[]>() {
            public int compare(int[] a, int[] b) {
                return a[0] - b[0];
            }
        });
        int n = matrix.length;
        for (int i = 0; i < n; i++) {
            queue.offer(new int[]{matrix[i][0], i, 0});
        }
        for (int i = 0; i < k - 1; i++) {
            int[] now = queue.poll();
            if (now[2] != n - 1) {
                queue.offer(new int[]{matrix[now[1]][now[2] + 1], now[1], now[2] + 1});
            }
        }
        return queue.poll()[0];
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