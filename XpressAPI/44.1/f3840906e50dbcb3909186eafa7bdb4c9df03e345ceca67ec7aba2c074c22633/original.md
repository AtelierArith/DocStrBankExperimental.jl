```
XPRSaddcbbariteration(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `bariteration`.
  * `action`: Defines a return value controlling barrier: <0continue with the next iteration; =0let barrier decide (use default stopping criteria); 1barrier stops with status not defined; 2barrier stops with optimal status; 3barrier stops with dual infeasible status; 4barrier stops wih primal infeasible status.

`cb` will be invoked with this signature:

```
cb(cbprob)::action
```
