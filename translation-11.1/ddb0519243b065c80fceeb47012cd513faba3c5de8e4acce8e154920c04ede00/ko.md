```
global
```

`global x`는 현재 범위와 그 내부 범위에서 `x`가 해당 이름의 전역 변수를 참조하도록 만듭니다. 더 많은 정보는 [변수 범위에 대한 매뉴얼 섹션](@ref scope-of-variables)을 참조하세요.

# 예제

```jldoctest
julia> z = 3
3

julia> function foo()
           global z = 6 # foo 외부에서 정의된 z 변수를 사용합니다.
       end
foo (generic function with 1 method)

julia> foo()
6

julia> z
6
```
