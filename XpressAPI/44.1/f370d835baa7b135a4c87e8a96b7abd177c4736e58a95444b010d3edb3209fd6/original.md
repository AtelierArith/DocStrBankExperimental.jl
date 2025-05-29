```
XPRS_MIPTERMINATIONMETHOD
```

Branch and Bound: How a MIP solve should be stopped on early termination when there are still active tasks in the system. (integer)

This can happen when, for example, a time or node limit is reached.

Default value: `0`

Values: 0 : Terminate tasks at the earliest opportunity. This can result in some unfinished node solves being discarded, although never integer solutions. 1 : Allow tasks to complete their current work but prevent new tasks from being started.
