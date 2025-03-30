```
rem(x::Integer, T::Type{<:Integer}) -> T
mod(x::Integer, T::Type{<:Integer}) -> T
%(x::Integer, T::Type{<:Integer}) -> T
```

`x` ≡ `y` (mod n) bul, burada n `T` içinde temsil edilebilen tam sayıların sayısıdır ve `y` `[typemin(T),typemax(T)]` aralığında bir tam sayıdır. Eğer `T` herhangi bir tam sayıyı temsil edebiliyorsa (örneğin `T == BigInt`), o zaman bu işlem `T`'ye bir dönüşüm ile eşdeğerdir.

# Örnekler

```jldoctest
julia> x = 129 % Int8
-127

julia> typeof(x)
Int8

julia> x = 129 % BigInt
129

julia> typeof(x)
BigInt
```
