```
XPRS_BACKGROUNDSELECT
```

Select which tasks to run in background jobs (for example in parallel to the root cut loop). (integer)

Default value: -1

Values are a bitset: bit 0 : Feasibility jump heuristic. bit 1 : Fast branch-and-bound heuristic. bit 2 : Same as bit 1 but with some additional heuristics enabled. bit 3 : Fix-propagate-repair heuristic.
