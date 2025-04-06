```
@spawn expr
```

Bir ifadeyi saran bir closure oluşturur ve bunu otomatik olarak seçilen bir süreçte çalıştırarak sonuca bir [`Future`](@ref) döner. Bu makro kullanımdan kaldırılmıştır; bunun yerine `@spawnat :any expr` kullanılmalıdır.

# Örnekler

```julia-repl
julia> addprocs(3);

julia> f = @spawn myid()
Future(2, 1, 5, nothing)

julia> fetch(f)
2

julia> f = @spawn myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    Julia 1.3 itibarıyla bu makro kullanımdan kaldırılmıştır. Bunun yerine `@spawnat :any` kullanın.

