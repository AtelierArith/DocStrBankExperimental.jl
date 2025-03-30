```
myid()
```

Mevcut işlemin kimliğini alır.

# Örnekler

```julia-repl
julia> myid()
1

julia> remotecall_fetch(() -> myid(), 4)
4
```
