```
@show exs...
```

Bir veya daha fazla ifadeyi ve sonuçlarını `stdout`'a yazdırır ve son sonucu döndürür.

Ayrıca bakınız: [`show`](@ref), [`@info`](@ref man-logging), [`println`](@ref).

# Örnekler

```jldoctest
julia> x = @show 1+2
1 + 2 = 3
3

julia> @show x^2 x/2;
x ^ 2 = 9
x / 2 = 1.5
```
