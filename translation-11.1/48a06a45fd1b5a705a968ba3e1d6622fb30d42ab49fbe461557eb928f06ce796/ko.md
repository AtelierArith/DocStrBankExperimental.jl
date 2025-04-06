```
undef
```

`UndefInitializer()`의 별칭으로, 배열 초기화에서 배열 생성 호출자가 초기화되지 않은 배열을 원한다는 것을 나타내기 위해 사용되는 단일 인스턴스 유형 [`UndefInitializer`](@ref)를 구성합니다.

참고: [`missing`](@ref), [`similar`](@ref).

# 예제

```julia-repl
julia> Array{Float64, 1}(undef, 3)
3-element Vector{Float64}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
