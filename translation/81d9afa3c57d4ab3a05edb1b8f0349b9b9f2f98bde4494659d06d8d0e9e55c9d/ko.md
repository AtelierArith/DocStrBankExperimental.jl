```
ScopedValue(x)
```

동적 범위에서 값을 전파하는 컨테이너를 만듭니다. [`with`](@ref)를 사용하여 새 동적 범위에 들어가고 생성합니다.

값은 새 동적 범위에 들어갈 때만 설정할 수 있으며, 참조된 값은 동적 범위의 실행 동안 일정합니다.

동적 범위는 작업 간에 전파됩니다.

# 예제

```jldoctest
julia> using Base.ScopedValues;

julia> const sval = ScopedValue(1);

julia> sval[]
1

julia> with(sval => 2) do
           sval[]
       end
2

julia> sval[]
1
```

!!! compat "Julia 1.11"
    Scoped values는 Julia 1.11에서 도입되었습니다. Julia 1.8+에서는 패키지 ScopedValues.jl에서 호환 가능한 구현을 사용할 수 있습니다.

