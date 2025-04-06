```
isassigned(ref::RefValue) -> Bool
```

주어진 [`Ref`](@ref)가 값과 연결되어 있는지 테스트합니다. 이는 비트 타입 객체의 [`Ref`](@ref)에 대해 항상 참입니다. 참조가 정의되지 않은 경우 `false`를 반환합니다.

# 예제

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
