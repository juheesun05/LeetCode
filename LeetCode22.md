class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> result;
        backtrack(result, "", 0, 0, n);
        return result;
    }

private:
    void backtrack(vector<string>& res, string current, int open, int close, int max) {
        // 현재 문자열의 길이가 n * 2일 때 
        if (current.length() == max * 2) {
            res.push_back(current);
            return;
        }

        // 여는 괄호를 추가할 수 있는 경우
        if (open < max) {
            backtrack(res, current + "(", open + 1, close, max);
        }

        // 닫는 괄호를 추가할 수 있는 경우 (여는 괄호보다 적게 썼을 때만)
        if (close < open) {
            backtrack(res, current + ")", open, close + 1, max);
        }
    }
};
