# Title: Implement MinMax Algorithm using divide and conquer Techniques
## Theory:
   We have to find the minimum and maximum element from the array. To do this we must use divide and conquer approach. Here remember key points
   1. if only one element is there i.e (x = y = a[i])
   2. if two elements are there then (min = a[j] && max = a[i]) if a[i]<[j] & vice versa
   3. Else calculate the mid term by (i+j)/2 & put min
   4. The Algorithm is as such
   ```
   Max - Min(x, y)
   if y – x <= 1 then
   return (max(numbers[x], numbers[y]),
   min((numbers[x], numbers[y]))
   else
   (max1, min1):= maxmin(x, ((x + y)/2))
   (max2, min2):= maxmin(((x + y)/2) + 1),y) return (max(max1,
   max2), min(min1, min2))
   
   ```
   
## Code:

    #include<stdio.h>
    #include<stdio.h>
    int max, min;
    int a[100];
    void maxmin(int i, int j)
    {
         int max1, min1, mid;
         if(i==j)
         {
            max = min = a[i];
         }
         else
          {
            if(i == j-1)
             {
               if(a[i] <a[j])
              {
                   max = a[j];
                   min = a[i];
               }
             else
               {
                   max = a[i];
                   min = a[j];
           }
       }
             else
               {
                   mid = (i+j)/2;
                   maxmin(i, mid);
                   max1 = max; min1 = min;
                   maxmin(mid+1, j);
                   if(max <max1)
                   max = max1;
                   if(min > min1)
                   min = min1;
            }
        }
     }
      int main ()
        {
          int i, num;
          printf ("\nEnter the total number of numbers : ");
          scanf ("%d",&num);
          printf ("Enter the numbers : \n");
       for (i=1;i<=num;i++)
        scanf ("%d",&a[i]);

        max = a[0];
        min = a[0];
        maxmin(1, num);
        printf ("Minimum element in an array : %d\n", min);
        printf ("Maximum element in an array : %d\n", max);
        return 0;
    }
    
