# Merge Sort

Job Posted: May 10, 2020 7:41 PM
Location: Mumbai

**Definition** **:**The Merge Sort is an efficient comparison based sorting algorithm based on divide and conquer strategy. It has a usual performance of Θ(N log N). Apart from the optimal speed, Merge Sort has found usage in parallel applications and seem to be the choice of sorting algorithm despite the tough competition posed by other optimal algorithms like Quick Sort. In fact, Merge sort does about 39% fewer comparisons than Quick Sort in the average case.

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
//Merge Sort's Implementation
package com.array.sortings;

public class MergeSort {
    public static void main(String[] args) {
 
        int[] intArray = {20, 35, -15, 7, 55, 1, -22};

        System.out.println("Unsorted Array");
        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }

        mergeSort(intArray, 0, intArray.length);

        System.out.println("Sorted Array");
        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }
    }

    //20, 35, -15, 7, 55, 1, -22
    public static void mergeSort(int[] input, int start, int end) { //This method is to Sort/ Split
        if (end - start < 2) {
            //<2 means one, and as we know that single array element is always sorted
            //As it doesn't have anyone to compared with... the number itself is sub sufficient
            return;
        }

        //Now we have to break the array into parts
        int mid = (start + end) / 2;    //mid = (0+7)/2 = 3
        //int this "end" it is always +1 then the last valid index in the array
        mergeSort(input, start, mid);//Indices(0 to 2)
        //MergeSort on left array
        //This is recursive call, so when it will end... it would have handled whole left side of the array
        //Input will be the array always, because we are doing logical partitioning
        mergeSort(input, mid, end); //Indices (3 to 6)
        //MergeSort on right array
        merge(input, start, mid, end);
        //We always merge sorted/split partition
    }

    //20, 35, -15, 7, 55, 1, -22
    public static void merge(int[] input, int start, int mid, int end) {

        if (input[mid - 1] <= input[mid]) {
            return;
            //As we know that we always Merge sorted partition.
            //So, mid is the first element of Right side array and
            //mid-1 is the last element of Left side array
            //This is the example of Shortest merging sort when both the files just have to be stick together
            //1st Optimisation
            //([mid-1]=1 and mid=7) //from the sorted array
            //Because it will be like sorting the already sorted array
        }
        int i = start;
        int j = mid;
        int tempIndex = 0;

        int[] temp = new int[end - start];
        //Creating temporary array  for merging
        while (i < mid && j < end) {
            //Means when either i gets finished... or j get finished we drop out, as everting else which has not
            // been destroyed or over come tinn now would got added up into the last
            temp[tempIndex++] = input[i] <= input[j] ? input[i++] : input[j++];
            //we have <=(equals to) because merge sort is stable... if we will remove this... it will become unstable
        }

        System.arraycopy(input, i, input, start + tempIndex, mid - i);
        //tempIndex counts that how many elements we have handled
        //mid-i tells us the number of elements that we didn't copied over into the temp array from the left partition
        //2nd Optimisation (adding left over from right side directly to the array
        System.arraycopy(temp, 0, input, start, tempIndex);
    }

}
//The End
```

# Advantages of Shell Sort

- It is quicker for larger lists because unlike insertion and bubble sort it doesn't go through the whole list several times.
- It has a consistent running time, carries out different bits with similar times in a stage.

# Disadvantages of Shell Sort

- Slower comparative to the other sort algorithms for smaller tasks.
- goes through the whole process even i he list is sorted (just like insertion and bubble sort?)
- uses more memory space to store the sub elements of the initial split list.

# Uses of Shell Sort

- Merge Sort is useful for sorting linked lists in O(n Log n) time
- Merge sort can be implemented without extra space for linked lists
- Merge sort is used for counting inversions in a list
- Merge sort is used in external sorting
