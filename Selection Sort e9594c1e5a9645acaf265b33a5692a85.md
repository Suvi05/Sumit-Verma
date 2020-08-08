# Selection Sort

Job Posted: May 9, 2020 10:22 PM
Location: Mumbai

**Definition** **:**The selection sort algorithm sorts an array by repeatedly finding the minimum element (considering ascending order) from unsorted part and putting it at the beginning. The algorithm maintains two subarrays in a given array.

1) The subarray which is already sorted.
2) Remaining subarray which is unsorted.

In every iteration of selection sort, the minimum element (considering ascending order) from the unsorted subarray is picked and moved to the sorted subarray.

# Details of Selection Sort

- In this sorting we "**We select largest number in whole array and then swap it with the last unsorted element in that Array**".
- It is a in-Place Algorithm.
- In this we are **logically partitioning the array**, we don't have to create another array in order to perform the sort.
- We do create some variables during implementation, but that won't depend on the number of items we're sorting.(Like first 2 steps in adding sugar to tea, because those variables won't change the size of array).
- **O(n^2) time Complexity- Quadratic.**
- It will take 100 steps to sort 10 items,10,000 for 100 and so on...
- It doesn't have as much as swapping as in Bubble sort
- This is **Unstable Algorithm.**
- A sorting algorithm is said to be unstable if there are two or more objects with equal keys which don’t appear in same order before and after sorting.

# Implementation of Selection Sort

```java
//Selection Sort's Implementation
package com.array.sortings;

public class SelectionSort {
    public static void main(String[] args) {

        int[] intArray = {20, 35, -15, 7, 55, 1, -22};

        System.out.println("Unsorted Array");
        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }
        for (int lastUnsortedIndex = intArray.length - 1; lastUnsortedIndex > 0; lastUnsortedIndex--) {

            int largest = 0;
            for (int i = 0; i <= lastUnsortedIndex; i++) {
                if (intArray[i] > intArray[largest]) {
                    largest = i;
                }
                swap(intArray, largest, lastUnsortedIndex);
            }
        }
        System.out.println("Sorted Array");
        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }
    }

    public static void swap(int[] array, int i, int j) {
        //we are putting it as static because we will call it in main method
        //int[] array - is the array  we are sorting
        //i& j - indices of the elements which we want to swap

        if (i == j) {
            return;
        }
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }
}
//The End
```

# Advantages of Selection Sort

- The main advantage of the selection sort is that it performs well on a
small list.
- Furthermore, because it is an in-place sorting algorithm, no additional temporary storage is required beyond what is needed to hold
the original list.

# Disadvantages of Selection Sort

- The primary disadvantage of the selection sort is its poor efficiency when dealing with a huge list of items.
- Similar to the bubble sort, the selection sort requires n-squared number of steps for
sorting n elements.
- Additionally, its performance is easily influenced by the initial ordering of the items before the sorting process. Because of this, the selection sort is only suitable for a list of few elements that are in random order.

# Uses of Selection Sort

- Selection sort almost always **outperforms bubble sort and gnome sort**.
- Can be useful when ***memory write is a costly operation***.
- While selection sort is **preferable to insertion sort** in terms of **number of writes** (Θ(n) swaps versus Ο(n^2) swaps).
- It almost always far exceeds the number of writes that **cycle sort** makes, as cycle sort is theoretically optimal in the number of writes.
- This can be important if writes are significantly more expensive than reads, such as with **EEPROM or Flash memory**, where every write lessens the lifespan of the memory.