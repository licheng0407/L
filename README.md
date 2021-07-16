#include <stdio.h>
//insert
void insert(int arr[],int n) {  //key是往前插入的数字 
	int key = arr[n];
	int i = n;
	while( arr[i-1] > key ) {
		arr[i] = arr[i-1];
		i--;
		if (i == 0) {//前面的边界 
			break;
		}
	}
	arr[i] = key;
} 

void insertionSort(int arr[],int n){
	int i;
	for (i=1;i<n;i++) {
		insert(arr,i); //i是insert里的n
	}
}

//辅助函数：打印数组
void print ( int arr[], int n)
{
	for (int i = 0; i < n; i++)
	{
		printf("%d ", arr[i]);
	}
	printf("\n");
 } 
 
 //辅助函数: 交换变量值
void swap(int *a,int *b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
 } 
 
 //划分函数
int partition(int arr[],int low,int high)
{
	int i = low-1;
	int j = high;
	int pivot = arr[high];//选最后一个数为枢纽 
	
	while(1)//死循环 
	{
		while (arr[++i] < pivot);//从最开始向后找数 ++i先加一次，再取值 
		while (arr[--j] > pivot);
		//指针停下来 
		if (i < j)
		    swap(&arr[i], &arr[j]);
		else
		    break;
	}
	//把枢纽元素放到正确位置上
	swap(&arr[i], &arr[high]);
	return i;//返回枢纽位置 
 } 
 
 
 //快速排序
void qsort(int arr[], int low, int high)//数组 最小指针 最高指针 
{
 	if (low < high)
 	{
 		int mid = partition(arr, low, high);//划分函数 mid第一个划分之后元素 
 		qsort(arr, low, mid-1);//左边区 
 		qsort(arr, mid + 1, high);//右边区 
	 }
	 //swap(&arr[i], &arr[j]);
} 
 
  
 //快速排序入口
void quick_sort(int arr[],int n)
{
	qsort(arr, 0, n-1); //数组  第一个下标，最后一个下标 
} 

int main()
{
	int arr[] = {9, 5, 2, 11, 12, 4, 3, 1, 7};
 	int n = 9;//9个数 
 	print(arr, n);
	printf("选择quick-1还是insert-2？\n");
	int x;
	scanf("%d",&x);
	switch ( x )
	{
		case 1 :
			
		printf("你选了quick\n");
		quick_sort(arr, n);//快排 
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
