```
isassigned(ref::RefValue) -> Bool
```

Verilen [`Ref`](@ref) değerle ilişkilendirilip ilişkilendirilmediğini test eder. Bu, bir bitstype nesnesinin [`Ref`](@ref) için her zaman doğrudur. Referans tanımsızsa `false` döner.

# Örnekler

```jldoctest
julia> ref = Ref{Function}()
Base.RefValue{Function}(#undef)

julia> isassigned(ref)
false

julia> ref[] = (foobar(x) = x)
foobar (generic function with 1 method)

julia> isassigned(ref)
true

julia> isassigned(Ref{Int}())
true
```
