```
remotecall_fetch(f, id::Integer, args...; kwargs...)
```

`fetch(remotecall(...))` işlemini tek bir mesajda gerçekleştirin. Anahtar kelime argümanları, varsa, `f`'ye iletilir. Herhangi bir uzak istisna, [`RemoteException`](@ref) içinde yakalanır ve fırlatılır.

Ayrıca [`fetch`](@ref) ve [`remotecall`](@ref) ile de bakabilirsiniz.

# Örnekler

```julia-repl
$ julia -p 2

julia> remotecall_fetch(sqrt, 2, 4)
2.0

julia> remotecall_fetch(sqrt, 2, -4)
HATA: İşçi 2'de:
DomainError with -4.0:
sqrt, negatif bir reel argüman ile çağrıldığında yalnızca karmaşık bir argüman ile çağrıldığında karmaşık bir sonuç döndürecektir. sqrt(Complex(x)) denemeyi deneyin.
...
```
