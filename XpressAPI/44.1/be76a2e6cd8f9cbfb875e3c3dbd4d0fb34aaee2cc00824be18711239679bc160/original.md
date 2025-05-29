```
XPRS_TREEDIAGNOSTICS
```

A bit vector providing control over how various tree-management-related messages get printed in the tree log file during the branch-and-bound search. (integer)

Default value: `7`

Values are a bitset: bit 0 : Output regular summaries of current tree memory usage. bit 1 : Output messages whenever tree data is being written to tree file. bit 2 : Output progress messages while tree data is being written to the tree file, at an interval controlled by the TREEFILELOGINTERVAL control.
