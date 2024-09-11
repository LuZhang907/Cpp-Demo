# C++ 

## Arrays and Strings
* Two Sum: Given an array of intergers *nums* and an integer *target*, return *indices* of two numbers such that they add up to *target*.

```c
vector <int> twoSum(vector<int>&nums, int target){
    int n = nums.size();
    for(int i = 0; i < n; i++){
        for(int j=i+1;j<n;j++){
            if(nums[i]+nums[j]==target){
                return{i,j};
            }
        }
    }return{};
}
```

```c
vector<int> twoSum(vector<int>&nums, int target){
    unordered_map<int,int> numMap;
    int n = nums.size();

    for(int i=0;i<n;i++){
        complement = target - nums[i];
        if(numMap.count(complement)){
            return {numMap[complement],i};
        }
        numMap[nums[i]]=i;
    }return{};

}
```

* Add Two Numbers
you are given two *non-empty* linked lists representing two non-negative integers. The digits are stored in *reverse order*, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

```c
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2){
    ListNode* dummyHead = new ListNode(0);
    ListNode* tail = dymmyHead;
    int carry = 0;

    while(l1!=nullptr || l2 != nullptr || carry!=0){
        int digit1 = (l1 != nullptr) ? l1 -> val : 0;
        int digit2 = (l2 != nullptr) ? l2 -> val : 0;

        int sum = digit1+digit2+carry;
        int digit = sum%10;
        carry = carry/10;

        ListNode* newNode = new ListNode(digit);
        tail -> next = newNode;
        tail = tail -> next

        l1 = (l1 != nullptr)? l1 -> next:nullptr;
        l2 = (l2 != nullptr)? l2 -> next:nullptr;
    }
    ListNode * result = dummyHead -> next
    delete dummyHead;
    return result;

}
```
* Median of Two Sorted Arrays
Given two sorted array *nums1* and *nums2* of size *m* and *n8 respectively, return the median of the two sorted arrays. The overall run time complexity should be *O(log(m+n))*

   - merge and sort, time complexity O((n+m)*log(n+m))
   ```c
       double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        // Get the sizes of both input arrays.
        int n = nums1.size();
        int m = nums2.size();

        // Merge the arrays into a single sorted array.
        vector<int> merged;
        for (int i = 0; i < n; i++) {
            merged.push_back(nums1[i]);
        }
        for (int i = 0; i < m; i++) {
            merged.push_back(nums2[i]);
        }

        // Sort the merged array.
        sort(merged.begin(), merged.end());

        // Calculate the total number of elements in the merged array.
        int total = merged.size();

        if (total % 2 == 1) {
            // If the total number of elements is odd, return the middle element as the median.
            return static_cast<double>(merged[total / 2]);
        } else {
            // If the total number of elements is even, calculate the average of the two middle elements as the median.
            int middle1 = merged[total / 2 - 1];
            int middle2 = merged[total / 2];
            return (static_cast<double>(middle1) + static_cast<double>(middle2)) / 2.0;
        }
        
    }
   ```
   - Two Pointer Method, time complexity O(n+m)
   ```c
       double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int n = nums1.size();
        int m = nums2.size();
        int i = 0, j = 0, m1 = 0, m2 = 0;

        //find median
        for(int count = 0; count <= (n+m)/2; count++){
            m2 = m1;
            if(i != n && j != m){
                if(nums1[i]>nums2[j]){
                    m1 = nums2[j++];
                }else{
                    m1 = nums1[i++];
                }
            }else if(i<n){
                m1 = nums1[i++];
            }else{
                m1 = nums2[j++];
            }
        }
        //check if the sume of n and m is odd
        if((n+m)%2==1){
            return static_cast<double>(m1);
        }else{
            double ans = static_cast<double>(m1)+static_cast<double>(m2);
            return ans/2.0;
        }
    }
   ```

   - Binary Search, Time Complexity O(log(min(m,n)))
   ```c
       double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        if(nums1.size()>nums2.size()){
            return findMedianSortedArrays(nums2, nums1);
        }

        int m = nums1.size(), n = nums2.size();
        int left = 0, right = m;
        while(left<=right){
            int partitionA = (left+right)/2;
            int partitionB = (m+n+1)/2 -partitionA;

            int maxLeftA = (partitionA ==0)? INT_MIN : nums1[partitionA-1];
            int minRightA = (partitionA ==m)? INT_MAX : nums1[partitionA];
            int maxLeftB = (partitionB==0)? INT_MIN : nums2[partitionB-1];
            int minRightB = (partitionB == n)? INT_MAX : nums2[partitionB];

            if(maxLeftA <= minRightB && maxLeftB <= minRightA ){
                if((m+n)%2==0){
                    return (max(maxLeftA, maxLeftB)+min(minRightA,minRightB))/2.0;
                }else{
                    return max(maxLeftA, maxLeftB);
                }
            }else if(maxLeftA > minRightB){
                right = partitionA-1;
            }else{
                left = partitionA+1;
            }
        }return 0.0;

    }
   ```


# Notes
* Syntax of Ternary Operator:
(condition)? expression_if_true:expression_if_false;

* Linked list
```c
Node* list = new Node;
(*list).data = "somedata"; //update value
(*list).next = nullptr;

//easier version
Node* list = new Node;
list -> data = "somedata"; 
list -> next = "nullptr";
```

* Common linked lists operations
 - Traversal
 - Rewiring(rearrange the elements)
 - Insertion
 - Deletion



# Data Structures

## abstract data types
* Queue, FIFO, enqueue, dequeue, enqueue
```c
const int CAPACITY = 50;

typedef struct
{
    person people[CAPACITY];
    int size;

}queue;
```

* stacks, LIFO (last in, first out), emails on outlook, most recent data first, push, pop

```c
typedef struct
{
    person people[CAPACITY];
    int size;
}stack;
```
 
* arrays, store data contingous

```c
#include <stdioh>
#include <stdlib.h> //malloc
int main(void){
    int *list = malloc(3*sizeof(int));
    if(list == NULL){
        return 1;
    }
    //int list[3];
    list[0]=1;
    list[1]=3;
    list[2]=3;

    int *tmp = malloc(4*sizeof(int));
    if(temp == NULL){
        free(list);
        return 1;
    }

    for(int i=0;i<3;i++){
        temp[i]=list[i];
    }

    temp[3]=4;

    free(list);
    list = temp;

    for (int i=0;i<4;i++>){
        printf("%i\n",list[i]);
    }

    free(list);
    return 0;
}
```

## data structures

struct

$.$ operator

$*$  

->

* linked lists, more memory less time

```c
typedef struct node{
    int number;
    struct node *next; //* pointer
}node;
```

```c
node *list=NULL; //create a pointer
node *n = malloc(sizeof(node)); //create space, pointer n pointed to this space
//(*n).number = 1; // go to number filed, assign to 1, which equivalent to:
n -> number =1;
n -> next = NULL;
list = n;

n -> next = list;
list = n;
```
```c
#include<stdio.h>
#include<stdlib.h>
typedef struct node{
    int number;
    struct node *next;
}node;

int main(int argc, char *argv[]{
    node *list = NULL;
    
    for(int = 1; i<argc;i++){
        int number =atoi(argc[i]);
        node *n = malloc(sizeof(node));
        if(n==NULL){
            //free memory thus far
            return 1;
        }
        n -> number = number;
        n -> next = list;
        list = n;
    }
    //print whole list
    node *ptr = list;
    while (ptr ! = NULL){
        printf("%i\n", ptr->number);
        ptr = ptr -> next;
    }
})
```

* trees
   - binary search trees
   ```c
   typedef struct node{
    int number;
    struct node *left;
    struct node *right;
   }node;
   ```
   ```c
   bool search(node *tree, int number){
    if(tree == NULL){
        return false;
    }else if(number < tree -> number){
        return search(tree -> left, number);
    }else if(number > tree -> number){
        return search(tree ->right, number);
    }else if(number == tree -> number){
        return true;
    }
   }
   ```

* dictionaries, keys and values
   - hashing
   - hash function
   - hash tables, array of linked list
   ```c
   typedef struct node{
    char *name;
    char *number;
    struct node *next;
   }node;

   node *table[26];
   ```
* tries, a tree of arrays
 










