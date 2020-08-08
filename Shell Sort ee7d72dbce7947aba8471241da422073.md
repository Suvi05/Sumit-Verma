# Shell Sort

Job Posted: May 10, 2020 2:08 AM
Location: Mumbai

**Definition** **:**The Shell sort (also known as Shell's method) is an in-place comparison based sorting algorithm.

Shell Sort improves its time complexity by taking the advantage of the fact that using Insertion Sort on a partially sorted array results in less number of moves.

- It is a generalization of:
    - sorting by exchange (bubble sort)
    - sorting by insertion (insertion sort)

# Details of Shell Sort

- Insertion sort starts out by  saying that the first element is sorted. It grows the sorted partition  from left to right, and on each iteration it picks off the first element in the unsorted partition and it inserts in into the correct position in the sorted partition and it does that by shifting to right to make room for the new element
- Hint: Shadow Remains till it is finalized that yes it is suitable for that place.
- It is a in-Place Algorithm.
- In this we are **logically partitioning the array**, we don't have to create another array in order to perform the sort.
- We do create some variables during implementation, but that won't depend on the number of items we're sorting.(Like first 2 steps in adding sugar to tea, because those variables won't change the size of array).
- **O(n^2) time Complexity- Quadratic.**
- It will take 100 steps to sort 10 items,10,000 for 100 and so on...
- It doesn't have as much as swapping as in Bubble sort
- This is **Stable Algorithm.**
- A sorting algorithm is said to be stable if two objects with equal keys appear in the same order in the sorted output as they appear in the unsorted input.

# Implementation of Shell Sort

```java
//Shell Sort's Implementation
package com.array.sortings;

public class ShellSort {
    public static void main(String[] args) {

        int[] intArray = {20, 35, -15, 7, 55, 1, -22};

        for (int gap = intArray.length / 2; gap > 0; gap /= 2) {    //1st Extra Line than insertion Sort
            //Above loop is the only preliminary sorting and when  the value of gap will become 1,
            // the below code will start working like insertion sort

            for (int i = gap; i < intArray.length; i++) {

                int newElement = intArray[i];

                int j = i;  //This j is being used for traversing the array

                while (j >= gap && intArray[j - gap] > newElement) {
                    intArray[j] = intArray[j - gap];
                    j = j - gap;   //2nd Extra Line than insertion Sort
                }
                intArray[j] = newElement;  //Insertion Sort
            }
        }

        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }
    }
}
//The End
```

# Advantages of Shell Sort

- With improved Average time complexity, it is a very efficient algorithm for medium size arrays.
- It is better than Insertion sort and 5 times faster than Bubble sort.

# Disadvantages of Shell Sort

- It is a complex algorithm.
- Not that much efficient as Merge and quicksort.
- It is limited with small size arrays.
- With a large-size array, its performance becomes slow.

# Uses of Shell Sort

- Shell sort performs more operations and has higher cache miss ratio than quicksort.
- However, since it can be implemented using little code and does not
use the call stack, some implementations of the q sort function in the C
standard library targeted at embedded systems use it instead of
quicksort. Shell sort is, for example, used in the uClibc library. For
similar reasons, an implementation of Shell sort is present in the Linux
kernel.
- Shell sort can also serve as a sub-algorithm of introspective sort,
to sort short subarrays and to prevent a slowdown when the recursion
depth exceeds a given limit. This principle is employed, for instance,
in the bzip2 compressor.