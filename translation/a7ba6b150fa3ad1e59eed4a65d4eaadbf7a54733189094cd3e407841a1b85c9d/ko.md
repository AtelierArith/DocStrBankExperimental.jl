```
x && y
```

단락 평가 불리언 AND.

또한 [`&`](@ref), 삼항 연산자 `? :`, 및 [제어 흐름](@ref man-conditional-evaluation) 매뉴얼 섹션을 참조하십시오.

# 예제

```jldoctest
julia> x = 3;

julia> x > 1 && x < 10 && x isa Int
true

julia> x < 0 && error("expected positive x")
false
```
