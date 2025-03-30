```
@isdefined s -> Bool
```

Değişken `s`'nin mevcut kapsamda tanımlı olup olmadığını test eder.

Ayrıca [`isdefined`](@ref) alan özellikleri için ve dizi indeksleri için [`isassigned`](@ref) veya diğer eşlemeler için [`haskey`](@ref) bakınız.

# Örnekler

```jldoctest
julia> @isdefined newvar
false

julia> newvar = 1
1

julia> @isdefined newvar
true

julia> function f()
           println(@isdefined x)
           x = 3
           println(@isdefined x)
       end
f (generic function with 1 method)

julia> f()
false
true
```
