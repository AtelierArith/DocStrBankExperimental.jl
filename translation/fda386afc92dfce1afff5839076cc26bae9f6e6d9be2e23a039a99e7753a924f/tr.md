```
Base64EncodePipe(ostream)
```

Yeni bir yazma-yalnızca I/O akışı döndürür; bu akışa yazılan herhangi bir baytı, `ostream`'e yazılan base64 kodlu ASCII baytlarına dönüştürür. `Base64EncodePipe` akışında [`close`](@ref) çağrısı yapmak, kodlamayı tamamlamak için gereklidir (ancak `ostream`'i kapatmaz).

# Örnekler

```jldoctest
julia> io = IOBuffer();

julia> iob64_encode = Base64EncodePipe(io);

julia> write(iob64_encode, "Hello!")
6

julia> close(iob64_encode);

julia> str = String(take!(io))
"SGVsbG8h"

julia> String(base64decode(str))
"Hello!"
```
