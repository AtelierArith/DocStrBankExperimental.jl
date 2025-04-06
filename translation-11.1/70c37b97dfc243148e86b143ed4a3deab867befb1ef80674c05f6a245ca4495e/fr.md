```
stacktrace([trace::Vector{Ptr{Cvoid}},] [c_funcs::Bool=false]) -> StackTrace
```

Renvoie une trace de pile sous la forme d'un vecteur de `StackFrame`s. (Par défaut, stacktrace ne renvoie pas les fonctions C, mais cela peut être activé.) Lorsqu'il est appelé sans spécifier de trace, `stacktrace` appelle d'abord `backtrace`.
