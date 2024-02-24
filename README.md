Block Swapping Algorithm for array rotation
In this article we will learn about C++ Program for Block Swapping Algorithm. Block swap algorithm is one of the efficient algorithm used for array rotation. We will discuss the recursive and iterative approaches in this page.

Block Swapping Algorithm for array rotation
While loop in C
Here, we will discuss the following two methods for block swapping algorithms.

Method 1 : Recursive Way
Method 2 : Iterative Way
Method 1 :
Declare two arrays A and B,
Copy all the elements from index 0 to (d-1) to A[] and from index d to n-1 to B[].
Run a loop till size of array A is equal to size of B[].
If A is longer, divide A into Al and Ar such that Al is of same length as B Swap Al and B to change AlArB into BArAl.
Now B is at its final place, so recur on pieces of A. 
Finally when A and B are of equal size, block swap them.
Method 1 : Code in C++
#include<iostream>
using namespace std;

void swap(int arr[], int fi, int si, int d);
 
void leftRotate(int arr[], int d, int n)
{
    if(d == 0 || d == n)
        return;
    
    if(d > n)
        d = d % n;
    
    if(n - d == d){
        swap(arr, 0, n - d, d);
        return;
    }
         
    if(d < n - d)
    {
    a    swap(arr, 0, n - d, d);
        leftRotate(arr, d, n - d);    
    }
    else{
        swap(arr, 0, d, n - d);
        leftRotate(arr + n - d, 2 * d - n, d);
    }
}
 

void swap(int arr[], int fi, int si, int d)
{
   int i, temp;
   for(i = 0; i<d; i++)  
   {
     temp = arr[fi + i];
     arr[fi + i] = arr[si + i];
     arr[si + i] = temp;
   }    
}    
 
/* Driver program to test above functions */
int main()
{
   int arr[] = {10, 20, 30, 40, 50, 60, 70};
   leftRotate(arr, 2, 7);
   
   for(int i = 0; i < 7; i++)
    cout<< arr[i]<<" ";
   
   return 0;
}   
Output
30 40 50 60 70 10 20
Method 2 :
In this method we implement the iterative approach for the algorithm discussed in method 1.

Method 2 : Code in C++
#include<iostream>
using namespace std;

void swap(int arr[], int fi, int si, int d);
 
void leftRotate(int arr[], int d, int n)
{
    int i, j;
    if(d == 0 || d == n)
        return;
  
    if(d > n)
        d = d % n;
    
    i = d;
    j = n - d;
    
    while (i != j){
        if(i < j) {
            swap(arr, d-i, d+j-i, i);
            j -= i;
        }
        else {
            swap(arr, d-i, d, j);
            i -= j;
        }
    }
  
    swap(arr, d-i, d, i);
}
 

void swap(int arr[], int fi, int si, int d)
{
   int i, temp;
   for(i = 0; i<d; i++)  
   {
     temp = arr[fi + i];
     arr[fi + i] = arr[si + i];
     arr[si + i] = temp;
   }    
}    
 
/* Driver program to test above functions */
int main()
{
   int arr[] = {10, 20, 30, 40, 50, 60, 70};
   leftRotate(arr, 2, 7);
   
   for(int i = 0; i < 7; i++)
    cout<< arr[i]<<" ";
   
   return 0;
}   
Output
30 40 50 60 70 10 20
