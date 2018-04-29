---
layout: post
title: Leetcode21 Merge Two Sorted Lists
tags: [Leetcode]
---
TMerge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

<!--excerpt-->

For example:

```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

Approach:


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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if (l1 == NULL && l2 == NULL) {
            return l1;
        }
        ListNode* ret = new ListNode(0);
        ListNode* record = ret;
        int count = 0;
        while (l1 != NULL || l2 != NULL) {
            if (l1 != NULL && l2 != NULL) {
                if (l1->val < l2->val) {
                    record->val = l1->val;
                    l1 = l1->next;
                    record->next = new ListNode(0);
                    record = record->next;
                } else {
                    record->val = l2->val;
                    l2 = l2->next;
                    record->next = new ListNode(0);
                    record = record->next;
                }
            }
            if (l1 == NULL && l2 != NULL) {
                record->val = l2->val;
                l2 = l2->next;
                if (l2 != NULL) {
                    record->next = new ListNode(0);
                    record = record->next;
                }
            }
            if (l1 != NULL && l2 == NULL) {
                record->val = l1->val;
                l1 = l1->next;
                if (l1 != NULL) {
                    record->next = new ListNode(0);
                    record = record->next;
                }
            }
        }
        return ret;
    }
};
```

Conclusion:
I have learned and reviewed several things from this question: