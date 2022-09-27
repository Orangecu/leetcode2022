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

leetcode 57
3sum
```java
public class Solution {
    /**
     * @param numbers: Give an array numbers of n integer
     * @return: Find all unique triplets in the array which gives the sum of zero.
     *          we will sort your return value in output
     */
    public List<List<Integer>> threeSum(int[] numbers) {
        // write your code here
        List<List<Integer>> result = new ArrayList<>();

        if (numbers.length < 3 || numbers == null) {
            return null;
        }
        
        Arrays.sort(numbers);
        
        for ( int i = 0; i < numbers.length - 2; i++) {
            if (i > 0 && numbers[i] == numbers[i - 1]) {
                continue;
            }
            int target  = -numbers[i];
            int start = i + 1;
            int end = numbers.length - 1;

            twoSum(numbers, start, end, target, result);
        }
        return result;
    }
    private void twoSum(int[] numbers, int start, int end, int target, List<List<Integer>> result) {
        while (start < end) {
            if ( numbers[start] + numbers[end] == target) {
                ArrayList<Integer> three = new ArrayList<>();
                three.add(-target);
                three.add(numbers [start]);
                three.add(numbers [end]);
                result.add(three);

                start++;
                end--;

                while (start < end && numbers[start] == numbers[start - 1]) {
                    start++;
                }
                while (end > start && numbers[end] == numbers[end + 1]) {
                    end--;
                }
            } else if (numbers[start] + numbers[end] < target) {
                start++;
            } else {
                end--;
            }
        }
    }
}
```

lintcode 443
2sum II
```java
public class Solution {
    /**
     * @param nums: an array of integer
     * @param target: An integer
     * @return: an integer
     */
    public int twoSum2(int[] nums, int target) {

        if (nums == null || nums.length == 0) {
            return 0;
        }
        Arrays.sort(nums);
        int count = 0;
        int left = 0, right = nums.length - 1;
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

lintcode
382 · Triangle Count
```java
// O(n^2)
public class Solution {
    /**
     * @param S: A list of integers
     * @return: An integer
     */
    public int triangleCount(int[] S) {
        if (S == null || S.length < 3) {
            return 0;
        }
        Arrays.sort(S);
        int count = 0;
        for (int i = 2; i < S.length; i++) {
            count += getCount(S, i);
        }
        return count;
    }

    private int getCount(int[] array, int targetIndex) {
        int count = 0;
        int start = 0, end = targetIndex - 1;

        while (start < end) {. 
            if (array[start] + array[end] > array[targetIndex]) {
                count += end - start;
                end--;
            } else {
                start++;
            }
        }

        return count;
    }
}
```

LintCode 148
Sort Colors
```java
public class Solution {
    /**
     * @param nums: A list of integer which is 0, 1 or 2 
     * @return: nothing
     */
    public void sortColors(int[] nums) {
        int left = 0;
        int right = nums.length - 1;
        int mid = 0;

        while (mid <= right){
            if (nums[mid] == 0){
                swap(nums, mid, left);
                mid ++;
                left ++;
            }
            else if (nums[mid] == 2){
                swap(nums, mid, right);
                right --;
            }
            else{
                mid ++;
            }
        }
    }

    private void swap(int[] a, int i, int j) {
        int tmp = a[i];
        a[i] = a[j];
        a[j] = tmp;
    }
}
```

143 · Sort Colors II
```java

public class Solution {
    /**
     * @param colors: A list of integer
     * @param k: An integer
     * @return: nothing
     */
    public void sortColors2(int[] colors, int k) {
        // write your code here
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        
        for (int i = 0; i < colors.length; i++) {
            // colors[0] = 3
            int currentCount = map.getOrDefault(colors[i], 0);
            map.put(colors[i], currentCount + 1);
        }
        System.out.println(map);

        // (3:1), (2:4), (1:2)

        // [1, 1, 1, 1, 1, 1 ] 
        int index = 0; 
        for (int i = 1; i <= k; i++) {
            int count = map.getOrDefault(i, 0);
            for (int j = 0; j < count; j++) {
                colors[index] = i; 
                index++;
            }
        }
        // System.out.println(Arrays.toString(result));

        // for (int i = 0; i < colors.length; i++) {
        //     colors[i] = result[i];
        // }
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

        quickSort(a, 0, a.length - 1);
    }

    private void quickSort(int[] a, int left, int right) {
        if (left >= right) {
            return;
        }

        int start = left, end = right;
        int pivot = a[(start + end) / 2]; // a[2]

        while (start <= end) {
            while (start <= end && a[start] < pivot) {
                start++;
            }

            while (start <= end && a[end] > pivot) {
                end--;
            }

            if (start <= end) {
                swap(a, start, end);

                start++;
                end--;
            }
        }

        quickSort(a, left, end);
        quickSort(a, start, right);
    }

    private void swap(int[] a, int i, int j) {
        int temp = a[i];
        a[i] = a[j];
        a[j] = temp;
    }
}
```

144 · Interleaving Positive and Negative Numbers
```java
// O(n)
public class Solution {
    /*
     * @param A: An integer array.
     * @return: nothing
     */
    public void rerange(int[] A) {
        int negCount = partition(A);
        int posCount = A.length - negCount;

        if (posCount > negCount) {
            interleave(A, 0, A.length - 2);
        } else if (posCount < negCount) {
            interleave(A, 1, A.length - 1);
        } else {
            interleave(A, 0, A.length - 1);
        }
    }

    private int partition(int[] A) {
        int start = 0, end = A.length - 1;
        while (start <= end) {
            while (start <= end && A[start] < 0) {
                start++;
            }

            while (start <= end && A[end] > 0) {
                end--;
            }

            if (start <= end) {
                swap(A, start, end);
                start++;
                end--;
            }
        }

        return start;
    }

    private void swap(int[] A, int start, int end) {
        int temp = A[start];
        A[start] = A[end];
        A[end] = temp;
    }

    private void interleave(int[] A, int start, int end) {
        while (start < end) {
            swap(A, start, end);
            start = start + 2;
            end = end - 2;
        }
    }
}
```


461 · Kth Smallest Numbers in Unsorted Array
```java

public class Solution {
    public int kthSmallest(int k, int[] nums) {
        return quickSelect(nums, 0, nums.length - 1, k - 1);
    }

    public int quickSelect(int[] A, int start, int end, int k) {
        int (start == end) {
            return A[start];
        }

        int left = start, right = end;
        int pivot = A[(start + end) / 2];

        while (left <= right) {
            while (left <= right && A[left] < pivot) {
                left++;
            }
            while (left <= right && A[right] > pivot) {
                right--;
            }
            if (left <= right) {
                int temp = A[left];
                A[left] = A[right];
                A[right] = temp;
                left++;
                right--;
            }
        }

        if (right >= k && start <= right) {
            return quickSelect(A, start, right, k);
        } else if (left <= k && left <= end) {
            return quickSelect(A, left, end, k);
        } else {
            return A[k];
        }
    }
}
```