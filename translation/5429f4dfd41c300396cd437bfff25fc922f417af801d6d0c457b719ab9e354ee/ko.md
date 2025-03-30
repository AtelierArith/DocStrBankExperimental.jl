```
WeakRef(x)
```

`w = WeakRef(x)`는 Julia 값 `x`에 대한 [약한 참조](https://en.wikipedia.org/wiki/Weak_reference)를 생성합니다: `w`가 `x`에 대한 참조를 포함하고 있지만, `x`가 가비지 컬렉션되는 것을 방지하지는 않습니다. `w.value`는 `x`가 아직 가비지 컬렉션되지 않았다면 `x`이거나, `x`가 가비지 컬렉션되었다면 `nothing`입니다.

```jldoctest
julia> x = "a string"
"a string"

julia> w = WeakRef(x)
WeakRef("a string")

julia> GC.gc()

julia> w           # `x`를 통해 참조가 유지됩니다.
WeakRef("a string")

julia> x = nothing # 참조를 지웁니다.

julia> GC.gc()

julia> w
WeakRef(nothing)
```
