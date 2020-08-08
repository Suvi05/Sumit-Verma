# Bubble Sort

Job Posted: May 9, 2020 5:09 PM
Location: Mumbai

**Definition** **:** Bubble sort, sometimes referred to as sinking sort, is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted. The algorithm, which is a comparison sort, is named for the way smaller or larger elements "bubble" to the top of the list.

# Details of Bubble Sort

- Start comparing 2 elements from left side towards Right.
- Swap if right one is smaller than the left one.
- This sorting is called Bubble Sorting because in this process the largest number gets bubbled up at Right side or any side.
- It is a in-Place Algorithm.
- In this we are logically partitioning the array, we don't have to create another array in order to perform the sort.
- We do create some variables during implementation, but that won't depend on the number of items we're sorting.(Like first 2 steps in adding sugar to tea, because those variables won't change the size of array).
- O(n^2) time Complexity- Quadratic.
- It will take 100 steps to sort 10 items,10,000 for 100 and so on...
- Algorithm degrades quickly as shown above.
- This is **Stable Algorithm.**
- A sorting algorithm is said to be stable if two objects with equal keys appear in the same order in the sorted output as they appear in the unsorted input.

# Implementation of Bubble Sort

```java
//Bubble Sort's Implementation
package com.array.sortings;

public class BubbleSort {
    public static void main(String[] args) {

        int[] intArray = {20, 35, -15, 7, 55, 1, -22};

        System.out.println("Unsorted Array");
        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }

        for (int lastUnsortedIndex = intArray.length - 1; lastUnsortedIndex > 0; lastUnsortedIndex--) {

            for (int i = 0; i < lastUnsortedIndex; i++)
                if (intArray[i] > intArray[i + 1]) {
                    swap(intArray, i, i + 1);
                }
        }
        //Doubt: What if intArray[i] is not greater than intArray[i+1]
        //Solution: Then without swapping it will come out of the loop and lastUnsortedIndex will get decremented

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
            //if i and j are equals than we don't have anything to swap
        }
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }
}
//The End
```

# Some more points related to Time Complexity

- The absolute worse case is it will take N squared steps, where N is the number of items we are sorting, But according to our code... it was not O(n^2) because in inner loops steps were reducing with each  out loop's execution, as sorted part was growing and inner loop was not touching the sorted part.
- But remember that, when it comes to determining the Time Complexity of an algorithm, we just try to get some sense of how the number of steps is growing as the number of items in the sort list grows.
- As per Time Complexity rule, the number of loops in this scenario is 2.
- Inner Loop + Outer Loop= 2 Loops, That's why also this is having O(n^2) time complexity.
- It is least efficient Algorithm.

# Advantages of Bubble Sort

- The primary advantage of the bubble sort is that it is popular and easy to implement.
- Furthermore, in the bubble sort, elements are swapped in place without using additional temporary storage, so the space requirement is at a minimum.

# Disadvantages of Bubble Sort

- The main disadvantage of the bubble sort is the fact that it does not deal well with a list containing a huge number of items.
- This is because the bubble sort requires n-squared processing steps for every n number of elements to be sorted.
- As such, the bubble sort is mostly suitable for academic teaching but not for real-life applications.

# Uses of Bubble Sort

- In **computer graphics**, it is popular for its
capability to detect a very small error (like swap of just two elements) in almost-sorted arrays and fix it with just linear complexity (2n).
- Bubble sort **interacts poorly with modern CPU hardware**. It produces at least:
    - **twice as many writes as insertion sort**
    - **twice as many cache misses**
    - **asymptotically more branch mispredictions**.
- Bubble sort is asymptotically equivalent in running time to insertion sort in the worst case, but the two algorithms differ greatly in the
number of swaps necessary.
- **Odd-Even sorts** and **Cocktail sorts** are improvements over Bubble sort.
- It is used in a **polygon filling algorithm**, where
bounding lines are sorted by their x coordinate at a specific scan line
(a line parallel to x axis) and with incrementing y their order changes
(two elements are swapped) only at intersections of two lines.