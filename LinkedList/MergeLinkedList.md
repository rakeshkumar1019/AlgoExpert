T.C : O(n) | S.C : O(n)

```cpp 
#include <vector>

using namespace std;

// This is an input class. Do not edit.
class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value) {
    this->value = value;
    next = nullptr;
  }
};

LinkedList *mergeLinkedLists(LinkedList *headOne, LinkedList *headTwo) {
  LinkedList *newHead = nullptr;
  LinkedList *newNode = nullptr;
  if( headOne == nullptr ){
    return headTwo;
  }
  if( headTwo == nullptr ){
    return headOne;
  }
  if( headOne->value < headTwo->value ){
     newNode = headOne;
     headOne = headOne->next;
  }else{
    newNode = headTwo;
    headTwo = headTwo->next;
  }
  newHead = newNode;

  while( headOne != nullptr && headTwo != nullptr ){
     if( headOne->value < headTwo->value ){
        newNode->next = headOne;
        newNode = newNode->next;
        headOne = headOne->next;
     }else{
        newNode->next = headTwo;
        newNode = newNode->next;
        headTwo = headTwo->next;
     }
  }
  while( headOne != nullptr ){
        newNode->next = headOne;
        newNode = newNode->next;
        headOne = headOne->next;
  }

  while( headTwo != nullptr ){
        newNode->next = headTwo;
        newNode = newNode->next;
        headTwo = headTwo->next;
  }

  return newHead;

}

```
