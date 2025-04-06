```
@locals()
```

호출 지점에서 정의된 모든 지역 변수의 이름(기호로)과 값을 포함하는 사전을 생성합니다.

!!! compat "Julia 1.1"
    이 매크로는 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest
julia> let x = 1, y = 2
           Base.@locals
       end
Dict{Symbol, Any} with 2 entries:
  :y => 2
  :x => 1

julia> function f(x)
           local y
           show(Base.@locals); println()
           for i = 1:1
               show(Base.@locals); println()
           end
           y = 2
           show(Base.@locals); println()
           nothing
       end;

julia> f(42)
Dict{Symbol, Any}(:x => 42)
Dict{Symbol, Any}(:i => 1, :x => 42)
Dict{Symbol, Any}(:y => 2, :x => 42)
```
