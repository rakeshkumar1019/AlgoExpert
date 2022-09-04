Question Link: https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list

Approch : Using Stack | T.c: O(N) | S.c :O(N) 
```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* prev;
    Node* next;
    Node* child;
};
*/

class Solution {
public:
    Node* flatten(Node* head) {
        if( head == nullptr ) return nullptr;
        stack<Node*> s;
        s.push(head);
        Node* prev = nullptr, *curr = nullptr, *newHead = nullptr;
        while( !s.empty() ){
            prev = curr;
            curr = s.top(); s.pop();  
            if( curr->next != nullptr ) {  
                s.push(curr->next);
            }
            if( curr->child != nullptr ){
                s.push(curr->child);
            }
            // Make changes to links now
            curr->child = nullptr;
            curr->prev = prev;
            if( prev != nullptr ){
                prev->next = curr;
            }else{
                newHead = curr;
            }
        }
        return newHead;
    }
};
```
