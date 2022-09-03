T.C :O(n) | S.C:(1)

```cpp
#include <vector>
using namespace std;

class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value);
  void addMany(vector<int> values);
  vector<int> getNodesInArray();
};

void removeKthNodeFromEnd(LinkedList *head, int k) {
  if( head == nullptr ) return;
  if( head->next == nullptr && k == 1 ) return;
  int count = 0;
  LinkedList *temp = head;
  while( temp != nullptr ){
    count++;
    temp = temp->next;
  }
  if( k > count ) return;
  //very import edge case 
  if( k == count ){
    head->value = head->next->value;
    head->next = head->next->next;
    return;
  }
  int prevIndex = count - k-1; 
  int c = 0;
  temp = head;
  while( temp != nullptr && c != prevIndex ){
     temp = temp->next;
     c = c + 1;
  }
  if( temp != nullptr && temp->next != nullptr ){
    LinkedList * del = temp->next;
    temp->next = temp->next->next;
    delete del;
  }
  return;
}

```
