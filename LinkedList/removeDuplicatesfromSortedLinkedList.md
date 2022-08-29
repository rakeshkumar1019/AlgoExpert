T.C : O(N)

S.C : O(1)

```cpp
using namespace std;

// This is an input struct. Do not edit.
class LinkedList {
public:
  int value;
  LinkedList *next = nullptr;

  LinkedList(int value) { this->value = value; }
};

LinkedList *removeDuplicatesFromLinkedList(LinkedList *linkedList) {
  if(linkedList == nullptr) return linkedList;

  LinkedList * currNode=linkedList;
  while( currNode->next != nullptr){
    LinkedList* temp= nullptr;
    if( currNode->value == currNode->next->value){
       temp = currNode->next;
       currNode->next = currNode->next->next;
       delete temp;
    }else{
      currNode=currNode->next;
    }
  }
  return linkedList;
}

```
