---
title: Insertion Sort
publish: true
date created: 2026-05-17
---
By iteration, we insert each element of an unsorted list into its correct position in a sorted portion of the list.
```java
import java.util.Scanner;
public class InsertionSort {
	public static int[] insertionSort(int[] arr){
		int n = arr.length;
		for(int i = 1; i < n; ++i){
			int key = arr[i];
			int j = i - 1;
			while(j >= 0 && arr[j] > key){
				arr[j+1] = arr[j];
				j = j - 1;
			}
			arr[j + 1] = key;
		}
	return arr;
	}
	public static void main(String[] args){
		Scanner input = new Scanner(System.in);
		int n = input.nextInt();
		int[] arr = new int[n];
		for(int i = 0; i < n;i++){
			arr[i] = input.nextInt();
		}
		int[] sortedArr = insertionSort(arr);
		for(int i = 0 ; i < n;i++){
			System.out.print(sortedArr[i] + " ");
		}
	}
}
```

# [Source](https://www.geeksforgeeks.org/dsa/insertion-sort-algorithm/)
[[Data-Structure]]