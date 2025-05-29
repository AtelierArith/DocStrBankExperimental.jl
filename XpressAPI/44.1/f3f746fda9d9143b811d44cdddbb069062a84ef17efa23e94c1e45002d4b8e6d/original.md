```
XPRSaddcbchgbranch(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `chgbranch`.
  * `entity`: A pointer to the variable or set on which to branch. Integer variables are identified by their column index, i.e. `0`, `1`,...(COLS`- 1`) and sets by their set index, i.e. `0`, `1`,...,(SETS`- 1`).
  * `up`: If `p_entity` is a variable, this is `1` if the upward branch is to be made first, or `0` otherwise. If `p_entity` is a set, this is `3` if the upward branch is to be made first, or `2` otherwise.
  * `estdeg`: This value is obsolete. It will be set to zero and any returned value is ignored.

`cb` will be invoked with this signature:

```
cb(cbprob, estdeg)::entity, up, estdeg
```
