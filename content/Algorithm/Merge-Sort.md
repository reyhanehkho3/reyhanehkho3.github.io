---
title: Merge Sort
publish: true
date created: 2026-05-17
---
It follows the divide and conquer approach. It divides the input array into 2 halves, recursively sorting the 2 halves and finally merging them back together.
```java
import java.util.Scanner;
public class MergeSort {
	public static void merge(int arr[], int left, int middle, int right) {
		int size1 = middle - left + 1;
		int size2 = right - middle;
		int Left[] = new int[size1];
		int Right[] = new int[size2];
		for (int i = 0; i < size1; i++)
			Left[i] = arr[left + i];
		for (int j = 0; j < size2; j++)
			Right[j] = arr[middle + 1 + j];
		int i = 0, j = 0, k = left;
		while (i < size1 && j < size2) {
			if (Left[i] <= Right[j])
				arr[k++] = Left[i++];
			else
				arr[k++] = Right[j++];
			}
		while (i < size1)
			arr[k++] = Left[i++];
		while (j < size2)
			arr[k++] = Right[j++]
	}
	public static void mergeSort(int arr[], int left, int right) {
		if (left < right) {
			int middle = left + (right - left) / 2;
			mergeSort(arr, left, middle);
			mergeSort(arr, middle + 1, right);
			merge(arr, left, middle, right);
		}
	}
	public static void main(String args[]) {
		Scanner input = new Scanner(System.in);
		int n = input.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++)
			arr[i] = input.nextInt();
		mergeSort(arr, 0, arr.length - 1);
		for (int i = 0; i < n; i++)
			System.out.print(arr[i] + " ");
	}
}
```

[[Data-Structure]]
[[Algorithm]]
# [Source](https://www.geeksforgeeks.org/dsa/merge-sort/)