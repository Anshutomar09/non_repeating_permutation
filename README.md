# non_repeating_permutation

class Solution {
public:
    void solve(vector<int>& nums, set<vector<int>>& ans,vector<int>temp, int ind){
         if(ind>=nums.size()){
             ans.insert(temp);
             return ;
         }
         for(int i=ind;i<nums.size();i++){
             swap(temp[ind], temp[i]);
             solve(nums, ans,temp, ind+1);
              swap(temp[ind], temp[i]);
         }
    }
    vector<vector<int>> permuteUnique(vector<int>& nums) {
         vector<int>temp=nums;
         set<vector<int>>ans;//make a set to not get the repeated values
         vector<vector<int>>output;//for storing ans in a vector named output
         solve(nums, ans,temp, 0);
         for(auto it :ans){
             output.push_back(it);//storing the values of set to vector
         }
         return output;
    }
};
