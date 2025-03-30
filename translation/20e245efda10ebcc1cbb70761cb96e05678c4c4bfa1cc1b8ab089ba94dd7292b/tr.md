```
get!(f::Union{Function, Type}, collection, key)
```

Verilen anahtar için saklanan değeri döndürün veya anahtar için bir eşleme yoksa, `key => f()` saklayın ve `f()` döndürün.

Bu, `do` bloğu sözdizimi kullanılarak çağrılması amaçlanmıştır.

# Örnekler

```jldoctest
julia> squares = Dict{Int, Int}();

julia> function get_square!(d, i)
           get!(d, i) do
               i^2
           end
       end
get_square! (generic function with 1 method)

julia> get_square!(squares, 2)
4

julia> squares
Dict{Int64, Int64} with 1 entry:
  2 => 4
```
