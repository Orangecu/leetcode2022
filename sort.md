
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

int m = SetA.length
int n = SetB.length




Merge Two Sorted Arrays
```java
public class Solution {
    /**
     * @param a: sorted integer array A
     * @param b: sorted integer array B
     * @return: A new sorted integer array
     */
    public int[] mergeSortedArray(int[] a, int[] b) {
        // write your code here
        int m = a.length;
        int n = b.length;
        int[] result = new int [m + n];
        int indexa = 0;
        int indexb = 0;
        int index = 0;
        while (indexa < m && indexb < n) {
            if (a[indexa] < b[indexb]) {
                result[index] = a[indexa];
                result[index]++;
                a[indexa]++;
            } else {
                result[index] = b[indexb];
                result[index]++;
                b[indexb]++;
            }
        }
        while (indexa < m) {
            result[index++] = a[indexa++];
        }
        while (indexb < n) {
            result[index++] = a[indexa++];
        } 
        return result;
    }
}

```

474 · Lowest Common Ancestor II
```java

```