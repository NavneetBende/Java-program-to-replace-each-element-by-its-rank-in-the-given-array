Replace each element by its rank given in array
Here in this program we will learn about Java Program to replace each element by its rank in the given array and discussed it. Given an array of distinct integers, we need to replace each element of the array with its rank. The minimum value element will have the highest rank in the Array.

Replace each element of the array by its rank in the array in C++
While loop in C
Method Discussed :
Method 1 : Using Naive approach.
Method 2 : Using Hash-map.
Method 1 :
Create a copy of the given input array.
Sort the copied array.
Run a nested loop and find the position of the given array element in the sorted array.
And replace the element with the position.
Print the modified input array.
Method 1 : Code in Java
import java.util.*;
 
class Main {
 
    static void changeArr(int[] input)
    {
        // Copy input array into newArray
        int newArray[] = Arrays.copyOfRange(input, 0, input.length);
 
        // Sort newArray[] in ascending order
        Arrays.sort(newArray);
        for(int i=0; i< input.length; i++){
    
        for(int j=0; j< input.length; j++){
            if(newArray[j]==input[i])
            {
                input[i] = j+1;
                break;
            }
        }
    }
    }
 
    // Driver Code
    public static void main(String[] args)
    {
        // Given array arr[]
        int[] arr = { 100, 2, 70, 12 , 90};
 
        // Function Call
        changeArr(arr);
 
        // Print the array elements
        System.out.println(Arrays.toString(arr));
    }
}
Output
[5, 1, 3, 2, 4]
Method 2 :
Copy the given arr[ ].
Then sort that copied array in ascending order.
Then traverse in the copied array and put their rank in Hash Map by taking a rank variable.
If the element is not present then update rank of the element in Hash-Map and increment rank variable as well.
Traverse the given array arr[] assign the rank of each element using the rank stored in Hash Map.
Method 2 : Code in Java
import java.util.*;
 
class Main {
 
    static void changeArr(int[] input)
    {
        // Copy input array into newArray
        int newArray[] = Arrays.copyOfRange(input, 0, input.length);
 
        // Sort newArray[] in ascending order
        Arrays.sort(newArray);
        int i;
         
        // Map to store the rank of the array element
        Map ranks  = new HashMap<>();
 
        int rank = 1;
 
        for (int index = 0; index < newArray.length; index++) {
           
            int element = newArray[index];
            
            // Update rank of element
            if (ranks.get(element) == null) {
                ranks.put(element, rank);
                rank++;
            }
        }
 
        // Assign ranks to elements
        for (int index = 0; index < input.length; index++) {
 
            int element = input[index];
            input[index] = ranks.get(input[index]);
        }
    }
 
    // Driver Code
    public static void main(String[] args)
    {
        // Given array arr[]
        int[] arr = { 100, 2, 70, 12, 90 };
 
        // Function Call
        changeArr(arr);
 
        // Print the array elements
        System.out.println(Arrays.toString(arr));
    }
}
Output
[5, 1, 3, 2, 4]
