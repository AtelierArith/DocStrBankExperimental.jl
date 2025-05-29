```
XPRSaddcbprenode(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `prenode`.
  * `infeasible`: The feasibility status. If set to a nonzero value by the user, the current node will be declared infeasible by the Optimizer.

`cb` will be invoked with this signature:

```
cb(cbprob)::infeasible
```
