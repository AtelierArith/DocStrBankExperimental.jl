```
in!(x, s::AbstractSet) -> Bool
```

Eğer `x` `s` içinde ise, `true` döner. Aksi takdirde, `x`'i `s`'ye ekler ve `false` döner. Bu, `in(x, s) ? true : (push!(s, x); false)` ile eşdeğerdir, ancak daha verimli bir uygulamaya sahip olabilir.

Ayrıca bakınız: [`in`](@ref), [`push!`](@ref), [`Set`](@ref)

!!! compat "Julia 1.11"
    Bu fonksiyon en az 1.11 sürümünü gerektirir.


# Örnekler

```jldoctest; filter = r"^  [1234]$"
julia> s = Set{Any}([1, 2, 3]); in!(4, s)
false

julia> length(s)
4

julia> in!(0x04, s)
true

julia> s
Set{Any} with 4 elements:
  4
  2
  3
  1
```
