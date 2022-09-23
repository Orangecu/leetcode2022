8-23

leetCode.1
Two Sum
```java

class Solution {
    public int[ ] twoSum(int[ ] nums, int target) {
        for (int i = 0; i < nums.length; i++){
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[ j ] == target - nums[i]) {
                    return new int[ ] { i, j };
                }
            }
        }
        return null;
    }
}
```


leetCode.561
Array Partition
```java
class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);
        int maxSum = 0;
        for (int i = 0; i < nums.length; i += 2) {
            maxSum += nums[i];
        }
        return maxSum;
    }
}
```

leetcode.607
```java
// add: O(n), find: O(n)
public class TwoSum {
    
    public List<Integer> nums;
    public TwoSum() {
        nums = new ArrayList<Integer>();
    }

    public void add(int number) {
        nums.add(number);

        int index = nums.size() - 1;
        while (index > 0 && nums.get(index) < nums.get(index - 1)) {
            swap(nums, index, index - 1);
            index--;
        }
    }
    public boolean find(int value) {
        int start = 0, end = nums.size() - 1;

        while (start < end) {
            if (nums.get(start) + nums.get(end) == value) {
                return true;
            } else if (nums.get(start) + nums.get(end) < value) {
                start++;
            } else {
                end--;
            }
        }

        return false;
    }

    private void swap(List<Integer> nums, int i, int j) {
        int temp = nums.get(i);
        nums.set(i, nums.get(j));
        nums.set(j, temp);
    }
}
```
leetcode.608
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

        int start = 0, end = nums.length - 1;
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

        return new int[] {-1, -1};
    }
}
```
leetcode.609
```java
public class Solution {
    /**
     * @param nums: an array of integer
     * @param target: an integer
     * @return: an integer
     */
    public int twoSum5(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        Arrays.sort(nums);
        int left = 0, right = nums.length - 1;
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
