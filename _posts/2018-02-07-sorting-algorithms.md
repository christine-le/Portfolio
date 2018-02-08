---
title: "Analysis of Sorting Algorithms - Part 1"
categories:
  - Programming
tags:
  - Python
  - Algorithms
toc: true
---
As part of my efforts to brush up on algorithms, I most recently have been focusing on sorting algorithms.  This post offers a brief analysis between selection sort versus insertion sort and merge versus quick sort.  My implementations are also included in Python.

### Selection Sort and Insertion Sort
#### The algorithms
Selection sort and insertion sort are both simple sorting algorithms.  They both sort elements in place, so no additional space is needed.  Also similarly, both algorithms have a time complexity of O(n^2^) due to their nested looping.  Therefore, the downside to these simple algorithms is that they do not perform well on large data sets. 

Selection sort operates by iterating through a list from left to right, and continually swapping the current item (aka, the left-most, unsorted item) with the latest, smallest item in the list.  Once the end of the list is reached, the list will then be fully sorted.

Insertion sort operates by iterating through a list from left to right, and taking the current item (again, the left-most, unsorted item) and scanning the sorted, left portion of the array to insert the item in its proper, sorted position.  The best example for this sort is to visualize physically sorting a set of cards in your hands.

#### The implementations
{% highlight python %}
def selection_sort(arr):
    for i in range(0, len(arr)):
        minIdx = i
        for j in range(i+1, len(arr)):
            if arr[j] < arr[minIdx]:
                minIdx = j
        # Swap
        tmp = arr[i]
        arr[i] = arr[minIdx]
        arr[minIdx] = tmp
    return arr
{% endhighlight %}

{% highlight python %}
def insertion_sort(arr):
    for i in range(1, len(arr)):
        curr = i
        val = arr[i]
        while val < arr[curr-1] and curr > 0:
            arr[curr] = arr[curr-1]
            curr -= 1
        arr[curr] = val
    return arr
{% endhighlight %}

### Merge Sort and Quick Sort
#### The algorithms
Merge sort and quick sort both uses a divide and conquer technique, making for efficient sorting on large arrays.  The time complexity is much better compared to selection, O(n^2^), and insertion, O(n^2^),  sorts.  The worst case for merge sort is O(n log n).  For quick sort, the worst case is O(n^2^).  However, on _average_, its complexity is O(n log n).  Lastly, both algorithms can naturally be written recursively.  

Some key differences to note are:  merge sort creates **sub-arrays** as it divides and conquers, while quick sort will sort **in place**.  Therefore, quick sort takes up less space as it does not require additional data structures for sorting.  

In merge sort, note that the recursive function call takes place *before* the actual sorting.  The recursive calls in a merge sort takes care of the repeated division of arrays into smaller sub-arrays.  Each sub-array is then sorted before being merged back together.

On the other hand, for quick sort, the recursive function calls takes place *after* the bulk of the work.  The bulk of the work in a quick sort uses a partitioning scheme that selects a pivot element in the array.  Each half of the array to the left of the pivot and to the right of the pivot and then continually sorted in such a way that the pivot is placed in its correct order.  That is, all elements to the left of the pivot should be smaller than the pivot.  All elements to the right of the pivot should be larger than the pivot.

#### The implementations
{% highlight python %}
def merge_sort(arr):
    if len(arr) == 1:
        return arr

    new_array = []
    half = len(arr)/2
    arr1 = merge_sort(arr[0:half])    # Divides left half
    arr2 = merge_sort(arr[half:])     # Divides right half

    # Sort and merge subarrays
    new_array = []
    i =  j = 0
    while i < len(arr1) or j < len(arr2):   
        if arr1[i] < arr2[j]:
            new_array.append(arr1[i])
            i += 1
        else:
            new_array.append(arr2[j])
            j += 1

        if i == len(arr1):
            new_array = new_array + arr2[j:]
            break
        if j == len(arr2):
            new_array = new_array + arr1[i:]
            break

    return new_array
{% endhighlight %}

{% highlight python %}
def quick_sort(arr, l, p):
    if l < p:
        p = partition(arr, l, p)
        quick_sort(arr, l, p-1)
        quick_sort(arr, p+1, len(arr) - 1)
    return arr

def partition(arr, l, p):
    for r in range(l, p):
        if arr[r] <= arr[p]:
            temp = arr[r]
            arr[r] = arr[l]
            arr[l] = temp
            l += 1
            
    # Lastly, swap current position with pivot
    temp = arr[l]
    arr[l] = arr[p]
    arr[p] = temp
    return l        # New pivot position
{% endhighlight %}

### Conclusion
For the full code snippets, take a look at my sorting algorithms on my [repo](https://github.com/christine-le/algorithms/blob/master/sorting.py).  I will be adding more sorting algorithms later and will do a follow up post to include additional sorting algorithms (bubble sort, heap sort, etc).

