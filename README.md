#include <stdio.h>
//insert
void insert(int arr[],int n) {  
	int key = arr[n];
	int i = n;
	while( arr[i-1] > key ) {
		arr[i] = arr[i-1];
		i--;
		if (i == 0) { 
			break;
		}
	}
	arr[i] = key;
} 

void insertionSort(int arr[],int n){
	int i;
	for (i=1;i<n;i++) {
		insert(arr,i); 
	}
}


void print ( int arr[], int n)
{
	for (int i = 0; i < n; i++)
	{
		printf("%d ", arr[i]);
	}
	printf("\n");
 } 
 

void swap(int *a,int *b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
 } 
 

int partition(int arr[],int low,int high)
{
	int i = low-1;
	int j = high;
	int pivot = arr[high];
	
	while(1)
	{
		while (arr[++i] < pivot);
		while (arr[--j] > pivot);
		 
		if (i < j)
		    swap(&arr[i], &arr[j]);
		else
		    break;
	}
	
	swap(&arr[i], &arr[high]);
	return i;
 } 
 
 

void qsort(int arr[], int low, int high)
{
 	if (low < high)
 	{
 		int mid = partition(arr, low, high); 
 		qsort(arr, low, mid-1);
 		qsort(arr, mid + 1, high);
	 }
	 //swap(&arr[i], &arr[j]);
} 
 
  

void quick_sort(int arr[],int n)
{
	qsort(arr, 0, n-1); 
} 

int main()
{
	int arr[] = {9, 5, 2, 11, 12, 4, 3, 1, 7};
 	int n = 9;
 	print(arr, n);
	printf("选择quick-1还是insert-2？\n");
	int x;
	scanf("%d",&x);
	switch ( x )
	{
		case 1 :
			
		printf("你选了quick\n");
		quick_sort(arr, n);
 	    print(arr, n);
 	    break;
 	    
 	    case 2 :
 	    	
		printf("你选了insert\n");
		insertionSort(arr, n);
	    print(arr, n);
	    break;
	default:
		printf("你选错了"); 
	}
}
