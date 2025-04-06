```
opnorm(A::Adjoint{<:Any,<:AbstractVector}, q::Real=2)
opnorm(A::Transpose{<:Any,<:AbstractVector}, q::Real=2)
```

Adjoint/Transpose ile sarılmış vektörler için, `A`'nın operatör $q$-normunu döndürün; bu, `p`-normu ile `p = q/(q-1)` değeri ile eşdeğerdir. `p = q = 2` olduğunda örtüşürler. `A`'nın bir vektör olarak `p` normunu hesaplamak için [`norm`](@ref) kullanın.

Bir vektör uzayı ile onun ikili arasındaki norm farkı, ikilik ve nokta çarpımı arasındaki ilişkiyi korumak için ortaya çıkar ve sonuç, `1 × n` matrisinin operatör `p`-normu ile tutarlıdır.

# Örnekler

```jldoctest
julia> v = [1; im];

julia> vc = v';

julia> opnorm(vc, 1)
1.0

julia> norm(vc, 1)
2.0

julia> norm(v, 1)
2.0

julia> opnorm(vc, 2)
1.4142135623730951

julia> norm(vc, 2)
1.4142135623730951

julia> norm(v, 2)
1.4142135623730951

julia> opnorm(vc, Inf)
2.0

julia> norm(vc, Inf)
1.0

julia> norm(v, Inf)
1.0
```
