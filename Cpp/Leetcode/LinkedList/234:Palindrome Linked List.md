> Given a singly linked list, determine if it is a palindrome.

**Follow up:**
Could you do it in O(n) time and O(1) space?



```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        
        vector<int> temp;
        ListNode *curr = head;
        
        while(curr){
            temp.push_back(curr->val);
            curr = curr->next;
        }
        
        int start = 0;
        int end = temp.size()-1;
        
        while(start <= end){
            if(temp[start] != temp[end]) return false;
            else{
                start++;
                end--;
            }
        }
        
        return true;
    }
};
```

