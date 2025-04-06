```
local
```

`local`은 새로운 지역 변수를 도입합니다. 더 많은 정보는 [변수 범위에 대한 매뉴얼 섹션](@ref scope-of-variables)을 참조하세요.

# 예제

```jldoctest
julia> function foo(n)
           x = 0
           for i = 1:n
               local x # 루프 지역 x 도입
               x = i
           end
           x
       end
foo (generic function with 1 method)

julia> foo(10)
0
```
