```
gradtape(f, args...; ctx=GradCtx(), seed=1)
gradtape!(tape::Tape; seed=1)
```

Calculate and record to the tape gradients of `tape[tape.resultid]` w.r.t. `Input` nodes. See grad() for more high-level API.
