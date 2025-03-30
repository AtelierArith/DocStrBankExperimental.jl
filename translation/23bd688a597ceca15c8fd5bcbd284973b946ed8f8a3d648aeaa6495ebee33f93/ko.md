```
isconcretetype(T)
```

타입 `T`가 구체적인 타입인지 여부를 결정합니다. 즉, 직접적인 인스턴스(값 `x`가 `typeof(x) === T`인 경우)를 가질 수 있음을 의미합니다. `isabstracttype(T)`의 부정이 아님에 유의하십시오. `T`가 타입이 아닌 경우 `false`를 반환합니다.

참고: [`isbits`](@ref), [`isabstracttype`](@ref), [`issingletontype`](@ref).

# 예제

```jldoctest
julia> isconcretetype(Complex)
false

julia> isconcretetype(Complex{Float32})
true

julia> isconcretetype(Vector{Complex})
true

julia> isconcretetype(Vector{Complex{Float32}})
true

julia> isconcretetype(Union{})
false

julia> isconcretetype(Union{Int,String})
false
```
