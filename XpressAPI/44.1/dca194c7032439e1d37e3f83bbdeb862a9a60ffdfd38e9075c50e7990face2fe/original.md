```
XPRS_RELAXTREEMEMORYLIMIT
```

When the memory used by the branch and bound search tree exceeds the target specified by the TREEMEMORYLIMIT control, the optimizer will try to reduce this by writing nodes to the tree file. (double)

In rare cases, usually where the solve has many millions of very small nodes, the tree structural data (which cannot be written to the tree file) will grow large enough to approach or exceed the tree's memory target. When this happens, optimizer performance can degrade greatly as the solver makes heavy use of the tree file in preference to memory. To prevent this, the solver will automatically relax the tree memory limit when it detects this case; the `RELAXTREEMEMORYLIMIT` control specifies the proportion of the previous memory limit by which to relax it. Set `RELAXTREEMEMORYLIMIT` to `0.0` to force the Xpress Optimizer to never relax the tree memory limit in this way.

Default value: `0.1`

Domain: [0.0,+1.0]
