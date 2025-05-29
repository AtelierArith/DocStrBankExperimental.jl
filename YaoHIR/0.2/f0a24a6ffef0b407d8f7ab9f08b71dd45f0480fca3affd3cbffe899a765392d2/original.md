```
GenericRoutine{name} <: Function
```

A `GenericRoutine` cannot be directly execute on a quantum device. It is a Julia `Function` that returns `Operation`, and `Operation` can be executed on quanutm device.

!!! note
    An instance of `GenericRoutine` should be treated like `Function`.

