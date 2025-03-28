```
mapfoldr(f, op, itr; [init])
```

Como [`mapreduce`](@ref), pero con asociatividad a la derecha garantizada, como en [`foldr`](@ref). Si se proporciona, el argumento de palabra clave `init` se utilizará exactamente una vez. En general, será necesario proporcionar `init` para trabajar con colecciones vacías.
