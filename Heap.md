leetcode
215
Kth Largest Element in an Array
```java

class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();
        //PriorityQueue里 首先弹出的永远是最小的数字
        for (int i = 0; i < k; i ++) {
            minHeap.add(nums[i]);
        } 
        for (int j = k; j < nums.length; j++) {
            if (nums[j] > minHeap.peek()) { //用最前面的数字（最小数）去和新的数比，如果新的数字大
                minHeap.poll(); //就弹出最小数字（最小数后面的 第二小数字进入最小数位置）
                minHeap.add(nums[j]); //再把最新的数字加入这个
            }
        }
        return minHeap.peek();
    }
}
```
简单解法

```java

class Solution {
    public int findKthLargest(int[] nums, int k) {
        Arrays.sort(nums);
        return nums[nums.length-k];
    }
}
```