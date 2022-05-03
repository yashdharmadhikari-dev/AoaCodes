## Title: To implement Binary Search

## Theory:
   Binary Search works on the principle of divide and conquer. Here we divide the bigger problem into subproblem and then solve them.
   1. Time Complexity - O(log n).
   2. Requires Elements in Sorted Order.
   3. It is very fast compared to linear search.
   4. Algorithm
       ``` 
        1. Compare x with the middle element.
        2. If x matches with the middle element, we
           return the mid index.
        3. Else If x is greater than the mid element, then
           x can only lie in the right half subarray after
           the mid element. So we recur for the right
           half.
        4. Else (x is smaller) recur for the left half.
        ```
        
## Code:
#### Iterative Approach:

    
    #include<stdio.h>
    void main(){
    int item,mid,lower = 0,total_n;
    printf("Enter number of elements: ");
    scanf("%d",&total_n);
    int arr[total_n],upper = total_n - 1,ex = total_n;
    printf("\nEnter the numbers in sorted order:");
    for(int i=0;i<total_n;i++){
        scanf("%d",&arr[i]);
    }
    printf("\nEnter the number to search: ");
    scanf("%d",&item);

    //actual code begins here
    mid = (lower+upper)/2;      //calculate mid

    while(arr[mid]!=item && lower <= upper){            //it will iterate until the item is not found and lower index is less than that of upper
        if(item>arr[mid])
            lower = mid + 1;
            else
            upper = mid - 1;

            mid = (lower+upper)/2;
    }

    if(arr[mid]==item)
        printf("Item %d found at location %d",item,mid+1);
        else
        printf("Item not Found");
       }
  
#### Recursive Approach:
    #include<stdio.h>
    int binarySearch(int arr[],int lower,int higher,int item){
    if(lower>higher)
        return -1;

        int mid = (lower+higher)/2;
        if(arr[mid]==item)
            return mid;
        else if(arr[mid]>item){
            binarySearch(arr,lower,mid-1,item);
        }
        else{
            binarySearch(arr,mid+1,higher,item);
        }
       }
       int main(void){
    int total_n;
    printf("Enter total number of elements:");
    scanf("%d",&total_n);
    int arr[total_n];
    printf("Enter the elements:");
    for(int i=0;i<total_n;i++){
        scanf("%d",&arr[i]);
    }
    int item;
    printf("Enter the item to search:");
    scanf("%d",&item);
    int lower = 0, higher = total_n - 1;
    int index = binarySearch(arr,lower,higher,item);
    if(index != -1)
        printf("Elements found at %d",index+1);
    else
        printf("Elements not found");
    }


