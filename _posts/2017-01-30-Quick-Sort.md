---
title: Quick Sort
---

### QuickSort Algorithm Tutorial


This Algorithm has a time complexity of **O(N\*logN)** and it's called _QuickSort_\.

QuickSort uses Divide-n-Conquer recursive algorithm to sort the values\.

#### Basic Idea of QuickSort


		1. Pick an element in the array as the pivot element.
		2. Make a pass to the array, called the PARTITION step, which rearranges the elements in the array:
			a. The pivot element is in the proper place
    		b. The elements less than pivot element are on the left of it
    		c. The elements greater than pivot element are on the right of it
		3. Recursively apply the above process to the left and right part of the pivot element.

#### Algorithm 

**Step 1.**  Choosing the Pivot Element

Choosing the pivot element can determine the complexity of the algorithm i.e. whether it will be **NlogN** or quadratic time:

		a. Normally we choose the first, last or the middle element as pivot. 
		   This can harm us badly as the pivot might end up to be the smallest or the largest element, 
		   thus leaving one of the partitions empty.

		b. We should choose the Median of the first, last and middle elements. 
		   If there are N elements, then the ceiling of N/2 is taken 
		   as the pivot element.

		_Example:_

**8, 3, 25, 6, 10, 17, 1, 2, 18, 5**

	First element: 	8
	Middle element: 10
	Last element: 	5

Therefore the median on **\[8,10,5\]** is 8.

**Step 2.**  Partitioning 

		a. First thing is to get the pivot out of the way and swapping it with the last number. 

		_Example: (shown using the above array elements)_

**5, 3, 25, 6, 10, 17, 1, 2, 18, 8**

		b. Now we want the elements greater than pivot to be on the right side of it and 
		   similarly the elements less than pivot to be on the left side of it.

		For this we define 2 pointers, namely i and j. 
		i being at the first index and j being and the last index of the array.

		* While i is less than j we keep in incrementing i until we find an element greater than pivot.
		* Similarly, while j is greater then i keep decrementing j  until we find an element less than pivot.
		* After both i and j stop we swap the elements at the indexes of i and j respectively.

		c. Restoring the pivot

		When the above steps are done correctly we will get this as our output:

**\[5, 3, 2, 6, 1\] \[8\] \[10, 25, 18, 17\]**

**Step 3.** Recursively Sort the left and right part of the pivot.

### C++ Code

```c++
int myints[] = {32, 71, 12, 45, 26, 80, 53, 33};
sort (myints.begin(), myints.begin()+7);  // 12 26 32 33 45 53 71 80
```


### Java Code

```java
public class QuickSortAlgorithm
{
	protected static int A[];

    public void sort(int[] A) {
        if (A == null || A.length == 0)
            return;
        quicksort(A, 0, A.length - 1);
    }

    public void quicksort(int[] A, int left, int right) {
        int pivot = A[left + (right - left) / 2];
        int i = left;
        int j = right;
        while (i <= j)
        {
            while (A[i] < pivot)
                i++;
            while (A[j] > pivot)
                j--;
            if (i <= j)
            {
                exchange(i, j);
                i++;
                j--;
            }
        }
        
        if (left < j)
            quicksort(A, left, j);
        if (i < right)
            quicksort(A, i, right);
    }

    public void exchange(int i, int j){
        int temp = A[i];
        A[i] = A[j];
        A[j] = temp;
    }
}
```
# Complexity of QuickSort

**Worst Case : O\(NlogN\)**
	This happens when the pivot is the smallest or the largest element. Then one of the partition is empty and we repeat the recursion for N-1 elements

**Best Case: O\(NlogN\)**
	This is when the pivot is the median of the array and the left and right part are the of the same size. There are **logN** partitions and to compare we do N comparisions

