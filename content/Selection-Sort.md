---
title: Selection Sort
publish: true
date created: 2026-05-17
---
It sorts by repeatedly selecting the smallest(or largest) element from the unsorted portion and swapping it with the first unsorted element. Here is the implementation:
```java
import java.util.Scanner;
public class SelectionSort{
	public static int[] selectionsort(int[] arr){
		int n = arr.length;
		for(int i = 0; i < n; i++){
			int min_index = i;
			for(int j = i + 1; j < n; j++){
				if(arr[j] < arr[min_index]){
					min_index = j;
				}
			}
		int temp = arr[i];
		arr[i] = arr[min_index];
		arr[min_index] = temp;
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
		int[] sortedArr = selectionsort(arr);
		for(int i = 0 ; i < n;i++){
			System.out.print(sortedArr[i] + " ");
		}
	}
}
```

[[Data-Structure]]
[[Algorithm]]
# [Source](https://www.geeksforgeeks.org/dsa/selection-sort-algorithm-2/)