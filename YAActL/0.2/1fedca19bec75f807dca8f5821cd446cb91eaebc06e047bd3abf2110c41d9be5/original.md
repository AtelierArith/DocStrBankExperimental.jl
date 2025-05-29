```
Dispatch
```

Depending on its `Dispatch` mode an actor composes the arguments  to the behavior function:

  * `full`: from the [`Become`](@ref) `args...` and the `msg.x...`.   This is the default dispatch mode.
  * `state`: from the actor state and the `msg.x...`. In this case the    actor updates its state with the result of the behavior   function. The result is saved in a `Tuple`.
