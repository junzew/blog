---
layout: post
title:  "Quick sort on singly linked list"
categories: algorithms 
---
```c
typedef struct Node {
    int val;
    struct Node* next;
} Node;

Node* partition(Node* lo, Node* hi) {
    Node* pivot = hi;
    Node* i = lo;
    for (Node* j = lo; j != hi; j = j->next) {
        if (j->val <= pivot->val) {
            int temp = i->val;
            i->val = j->val;
            j->val = temp;
            i = i->next;
        }
    }
    int temp = i->val;
    i->val = hi->val;
    hi->val = temp;
    return i;
}

void quicksort(Node* lo, Node* hi) {
    if (lo == NULL || hi == NULL || lo == hi) return;
    if (lo->next == hi && lo->val <= hi->val) return;
    if (lo != hi) {
        Node* p = partition(lo, hi);
        quicksort(lo, p);
        quicksort(p->next, hi);
    }
}
```


