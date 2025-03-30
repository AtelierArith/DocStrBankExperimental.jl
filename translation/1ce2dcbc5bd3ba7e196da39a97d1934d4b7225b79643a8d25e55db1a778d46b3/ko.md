```
@isdefined s -> Bool
```

변수 `s`가 현재 범위에서 정의되어 있는지 테스트합니다.

필드 속성에 대한 [`isdefined`](@ref)와 배열 인덱스에 대한 [`isassigned`](@ref) 또는 다른 매핑에 대한 [`haskey`](@ref)를 참조하세요.

# 예제

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
