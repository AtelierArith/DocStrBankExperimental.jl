```
@inferred [허용된유형] f(x)
```

호출 표현식 `f(x)`가 컴파일러에 의해 추론된 동일한 유형의 값을 반환하는지 테스트합니다. 이는 유형 안정성을 확인하는 데 유용합니다.

`f(x)`는 임의의 호출 표현식일 수 있습니다. 유형이 일치하면 `f(x)`의 결과를 반환하고, 다른 유형이 발견되면 `Error` `Result`를 반환합니다.

선택적으로, `허용된유형`은 테스트를 완화하여 `f(x)`의 유형이 `허용된유형`을 제외한 추론된 유형과 일치하거나, 반환 유형이 `허용된유형`의 하위 유형일 때 통과하도록 합니다. 이는 `Union{Nothing, T}` 또는 `Union{Missing, T}`와 같은 작은 유니온을 반환하는 함수의 유형 안정성을 테스트할 때 유용합니다.

```jldoctest; setup = :(using InteractiveUtils; using Base: >), filter = r"begin\n(.|\n)*end"
julia> f(a) = a > 1 ? 1 : 1.0
f (generic function with 1 method)

julia> typeof(f(2))
Int64

julia> @code_warntype f(2)
MethodInstance for f(::Int64)
  from f(a) @ Main none:1
Arguments
  #self#::Core.Const(f)
  a::Int64
Body::UNION{FLOAT64, INT64}
1 ─ %1 = (a > 1)::Bool
└──      goto #3 if not %1
2 ─      return 1
3 ─      return 1.0

julia> @inferred f(2)
ERROR: return type Int64 does not match inferred return type Union{Float64, Int64}
[...]

julia> @inferred max(1, 2)
2

julia> g(a) = a < 10 ? missing : 1.0
g (generic function with 1 method)

julia> @inferred g(20)
ERROR: return type Float64 does not match inferred return type Union{Missing, Float64}
[...]

julia> @inferred Missing g(20)
1.0

julia> h(a) = a < 10 ? missing : f(a)
h (generic function with 1 method)

julia> @inferred Missing h(20)
ERROR: return type Int64 does not match inferred return type Union{Missing, Float64, Int64}
[...]
```
