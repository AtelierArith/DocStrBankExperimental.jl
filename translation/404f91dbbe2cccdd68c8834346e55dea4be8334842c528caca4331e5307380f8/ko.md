```
applicable(f, args...) -> Bool
```

주어진 일반 함수가 주어진 인수에 적용 가능한 메서드를 가지고 있는지 여부를 결정합니다.

자세한 내용은 [`hasmethod`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> function f(x, y)
           x + y
       end;

julia> applicable(f, 1)
false

julia> applicable(f, 1, 2)
true
```
