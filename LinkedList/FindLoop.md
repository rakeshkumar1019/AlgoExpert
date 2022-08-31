APPROCH : USING MAP | time O(n) | space O(n)

```cpp
#include <vector>
using namespace std;

class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value);
};
//Using Map  time O(n) | space O(n)
LinkedList *findLoop(LinkedList *head) {
  if(head == nullptr) return head;
  LinkedList* curr =head;
  map<LinkedList*,bool> visited;
  while( curr != nullptr ){
    if( visited[curr] == true){
      return curr;
    }else{
      visited[curr] = true;
      curr = curr->next;
    }
  }
  return nullptr;
}

```

APPROCH : USING TWO POINTER  | time O(n) | space O(1)

```cpp
#include <vector>
using namespace std;

class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value);
};
LinkedList *isLoopExiest(LinkedList *head){
  if( head == nullptr ) return nullptr;
  if( head->next == nullptr ) return nullptr;
  if( head->next->next == nullptr ) return nullptr;
  LinkedList *slow = head->next;
  LinkedList *fast = head->next->next;
  while( slow != nullptr && fast != nullptr ){
    if( slow == fast ){
      return slow;
    }
    slow = slow->next;
    fast = fast->next;
    if( fast != nullptr ){
      fast = fast->next;
    }else{
      return nullptr;
    }
  }
  return nullptr;
}
//using two pointers slow & fast
LinkedList *findLoop(LinkedList *head) {
    if( head == nullptr ) return head;
    LinkedList *loopNode = isLoopExiest(head);
    if( loopNode != nullptr ){
        LinkedList *meetNode = loopNode;
        LinkedList *currNode = head;

        while( meetNode != currNode ){
          currNode = currNode->next;
          meetNode = meetNode->next;
        }      
        return meetNode; 
      
    }else{
      return nullptr;
    }
  return nullptr;
}

```
