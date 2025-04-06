```
Vararg{T,N}
```

Bir tuple türünün son parametresi [`Tuple`](@ref) özel değeri `Vararg` olabilir; bu, herhangi bir sayıda son elemanı belirtir. `Vararg{T,N}` tam olarak `N` adet `T` türünde elemanı ifade eder. Son olarak, `Vararg{T}` sıfır veya daha fazla `T` türünde elemanı ifade eder. `Vararg` tuple türleri, varargs yöntemleri tarafından kabul edilen argümanları temsil etmek için kullanılır (kılavuzdaki [Varargs Fonksiyonları](@ref) bölümüne bakın.)

Ayrıca [`NTuple`](@ref) ile ilgili bilgiye bakın.

# Örnekler

```jldoctest
julia> mytupletype = Tuple{AbstractString, Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```
