```
isready(rr::RemoteChannel, args...)
```

Determina si un [`RemoteChannel`](@ref) tiene un valor almacenado. Ten en cuenta que esta función puede causar condiciones de carrera, ya que para cuando recibas su resultado, puede que ya no sea cierto. Sin embargo, se puede usar de manera segura en un [`Future`](@ref) ya que solo se asignan una vez.
