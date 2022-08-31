Question Link: https://leetcode.com/problems/linked-list-cycle/

T.C : O(n)

S.C : O(1)

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
    bool hasCycle(ListNode *head) {
        if( head == nullptr ) return false;
        if( head->next == nullptr ) return false; // if one node exits
        if( head->next->next == nullptr ) return false; 
        ListNode *slow = head; //at 1st node
        ListNode *fast = head->next->next; // at 3rd node
        
        while( slow != nullptr && fast != nullptr ){
            if( slow == fast){
                return true;
            }
            slow = slow->next;
            fast = fast->next;
            if( fast != nullptr ){
                fast = fast->next; 
            }else{
                return false;
            }
        }
        return false;
    }
};
```
