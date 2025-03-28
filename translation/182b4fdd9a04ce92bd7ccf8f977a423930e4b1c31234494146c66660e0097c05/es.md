```
mapfoldl(f, op, itr; [init])
```

Como [`mapreduce`](@ref), pero con asociatividad izquierda garantizada, como en [`foldl`](@ref). Si se proporciona, el argumento clave `init` se utilizará exactamente una vez. En general, será necesario proporcionar `init` para trabajar con colecciones vacías.
