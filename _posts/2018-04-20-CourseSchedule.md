---
layout: post
title: Leetcode207 Course Schedule
tags: [Leetcode]
---
There are a total of n courses you have to take, labeled from 0 to n - 1.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: [0,1]

Given the total number of courses and a list of prerequisite pairs, is it possible for you to finish all courses?

<!--excerpt-->

For example:

```
2, [[1,0]]
There are a total of 2 courses to take. To take course 1 you should have finished course 0. So it is possible.
```

```
2, [[1,0],[0,1]]
There are a total of 2 courses to take. To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.
```

Note:
The input prerequisites is a graph represented by a list of edges, not adjacency matrices. Read more about how a graph is represented.
You may assume that there are no duplicate edges in the input prerequisites.
click to show more hints.

Hints:
This problem is equivalent to finding if a cycle exists in a directed graph. If a cycle exists, no topological ordering exists and therefore it will be impossible to take all courses.
Topological Sort via DFS - A great video tutorial (21 minutes) on Coursera explaining the basic concepts of Topological Sort.
Topological sort could also be done via BFS.


Approach:


Solution:

```C++
class Solution {
public:
    bool canFinish(int numCourses, vector<pair<int, int>>& prerequisites) {
        vector<vector<int>> graph(numCourses, vector<int>(0));
        vector<int> in_degree(numCourses, 0);

        for (auto course : prerequisites) {
            graph[course.second].push_back(course.first);
            ++in_degree[course.first];
        }

        queue<int> q;
        for (int i = 0; i < numCourses; i++) {
            if (in_degree[i] == 0) {
                q.push(i);
            }
        }

        while (!q.empty()) {
            int c = q.front();
            q.pop();
            for (auto p : graph[c]) {
                --in_degree[p];
                if (in_degree[p] == 0) q.push(p);
            }
        }

        for (int i = 0; i < numCourses; i ++) {
            if (in_degree[i] != 0) return false;
        }

        return true;
    }
};
```

Conclusion:
I have learned and reviewed several things from this question: