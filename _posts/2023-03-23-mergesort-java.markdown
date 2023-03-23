---
layout: post
title:  "(알고리즘)mergesort 자바"
date:   2023-03-23 13:20:46 +0900
categories: algorithm
tag: [algorithm]
---

# (Algorithm)Mergesort - Java 



```java
public class MergeSort {
    public static void mergeSort(int[] arr, int start, int end) {
        if (start < end) {
            int mid = (start + end) / 2;
            mergeSort(arr, start, mid);
            mergeSort(arr, mid + 1, end);
            merge(arr, start, mid, end);
        }
    }

    public static void merge(int[] arr, int start, int mid, int end) {
        int[] tempArr = new int[end - start + 1];
        int i = start;
        int j = mid + 1;
        int k = 0;

        while (i <= mid && j <= end) {
            if (arr[i] < arr[j]) {
                tempArr[k++] = arr[i++];
            } else {
                tempArr[k++] = arr[j++];
            }
        }

        while (i <= mid) {
            tempArr[k++] = arr[i++];
        }

        while (j <= end) {
            tempArr[k++] = arr[j++];
        }

        for (i = start; i <= end; i++) {
            arr[i] = tempArr[i - start];
        }
    }
}
```