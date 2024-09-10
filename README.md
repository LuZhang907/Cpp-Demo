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





