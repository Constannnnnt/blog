---
layout: post
title: Leetcode19 Remove Nth Node From End of List
tags: [Leetcode]
---
Given a linked list, remove the n-th node from the end of list and return its head.

<!--excerpt-->

For example:

```
Given linked list: 1->2->3->4->5, and n = 2.
After removing the second node from the end, the linked list becomes 1->2->3->5.
```

Solution:

```C++
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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if (!head || n == 0) return NULL;
        int size = 0;
        ListNode* cnt = head;
        while (cnt != NULL) {
            size += 1;
            cnt = cnt->next;
        }
        int idx = size - n + 1;
        if (idx <= 0) return NULL;
        int count = 0;
        ListNode* ret = new ListNode(0);
        ListNode* tmp = ret;
        cnt = head;
        while (cnt != NULL) {
            count += 1;
            if (count == idx) {
                cnt = cnt->next;
            }
            else {
                tmp->next = new ListNode(cnt->val);
                cnt = cnt->next;
                tmp = tmp->next;
            }
        }
        return ret->next;
    }
};
```

Follow Up: Could you do this in one pass?

Solution:

```C++

```

Conclusion:
I have learned and reviewed several things from this question: