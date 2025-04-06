```
@spawnat p expr
```

Bir ifadeyi sarmalayan bir closure oluşturun ve closure'ı işlem `p` üzerinde asenkron olarak çalıştırın. Sonuç için bir [`Future`](@ref) döndürün. Eğer `p` alıntılanmış sabit sembol `:any` ise, sistem otomatik olarak kullanılacak bir işlemci seçecektir.

# Örnekler

```julia-repl
julia> addprocs(3);

julia> f = @spawnat 2 myid()
Future(2, 1, 3, nothing)

julia> fetch(f)
2

julia> f = @spawnat :any myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    `:any` argümanı Julia 1.3 itibarıyla mevcuttur.

