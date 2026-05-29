---
title: Quick Sort
publish: true
date created: 2026-05-17
---
It is a sorting algorithm based on the Divide and Conquer that picks an element as a pivot and partitions the given array around the picked pivot by placing the pivot in its correct position in the sorted array. 
```java
import java.util.Scanner;
public class QuickSort {
	public static int partition(int[] arr, int low, int high){
		int pivot = arr[high];
		int i = low - 1;
		for(int j = low; j <= high -1; j++){
			if(arr[j] < pivot){
			i++;
			swap(arr,i , j);
			}
		}
		swap(arr, i+1, high);
		return i +1;
		}
	public static void swap(int[] arr, int i, int j){
		int temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
	}
	public static void quickSort(int[] arr, int low, int high){
		if(low < high){
		int pi = partition(arr, low, high);
		quickSort(arr, low, pi -1);
		quickSort(arr, pi + 1, high);
		}
	}
	public static void main(String args[]){
		Scanner input = new Scanner(System.in);
		int n = input.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++)
			arr[i] = input.nextInt();
		quickSort(arr, 0, arr.length - 1);
		for (int i = 0; i < n; i++)
			System.out.print(arr[i] + " ");
	}
}
```

[[Data-Structure]]
[[Algorithm]]
# [Source](https://www.geeksforgeeks.org/dsa/quick-sort-algorithm/)