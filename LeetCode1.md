cpp'''
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        // key: 숫자 값, value: 해당 숫자의 인덱스
        unordered_map<int, int> numMap;
        
        for (int i = 0; i < nums.size(); i++) {
            // 찾는값 계산
            int complement = target - nums[i];
            
            // 찾는값이 맵에 있는지 확인
            if (numMap.find(complement) != numMap.end()) {
                // 있으면 [찾는값의 인덱스, 현재 인덱스] 반환
                return {numMap[complement], i};
            }
            
            // 없으면 현재 숫자와 인덱스를 맵에 기록
            numMap[nums[i]] = i;
        }
        return {};
    }
};
