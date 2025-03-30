```
UndefInitializer
```

배열 초기화에 사용되는 싱글톤 타입으로, 배열 생성자가 초기화되지 않은 배열을 원한다는 것을 나타냅니다. 또한 [`undef`](@ref)를 참조하십시오. 이는 `UndefInitializer()`의 별칭입니다.

# 예제

```julia-repl
julia> Array{Float64, 1}(UndefInitializer(), 3)
3-element Array{Float64, 1}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
