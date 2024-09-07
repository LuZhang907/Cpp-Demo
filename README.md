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




