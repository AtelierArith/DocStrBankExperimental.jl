```
@Kwargs{key1::Type1, key2::Type2, ...}
```

이 매크로는 [`@NamedTuple`](@ref)와 동일한 구문에서 키워드 인수의 타입 표현을 구성하는 편리한 방법을 제공합니다. 예를 들어, `func([positional arguments]; kw1=1.0, kw2="2")`와 같은 함수 호출이 있을 때, 이 매크로를 사용하여 키워드 인수의 내부 타입 표현을 `@Kwargs{kw1::Float64, kw2::String}`으로 구성할 수 있습니다. 매크로 구문은 스택 추적 보기에서 인쇄될 때 키워드 메서드의 시그니처 타입을 단순화하도록 특별히 설계되었습니다.

```julia
julia> @Kwargs{init::Int} # 키워드 인수의 내부 표현
Base.Pairs{Symbol, Int64, Tuple{Symbol}, @NamedTuple{init::Int64}}

julia> sum("julia"; init=1)
ERROR: MethodError: no method matching +(::Char, ::Char)
함수 `+`는 존재하지만, 이 조합의 인수 타입에 대해 정의된 메서드는 없습니다.

가장 가까운 후보는:
  +(::Any, ::Any, ::Any, ::Any...)
   @ Base operators.jl:585
  +(::Integer, ::AbstractChar)
   @ Base char.jl:247
  +(::T, ::Integer) where T<:AbstractChar
   @ Base char.jl:237

스택 추적:
  [1] add_sum(x::Char, y::Char)
    @ Base ./reduce.jl:24
  [2] BottomRF
    @ Base ./reduce.jl:86 [인라인]
  [3] _foldl_impl(op::Base.BottomRF{typeof(Base.add_sum)}, init::Int64, itr::String)
    @ Base ./reduce.jl:62
  [4] foldl_impl(op::Base.BottomRF{typeof(Base.add_sum)}, nt::Int64, itr::String)
    @ Base ./reduce.jl:48 [인라인]
  [5] mapfoldl_impl(f::typeof(identity), op::typeof(Base.add_sum), nt::Int64, itr::String)
    @ Base ./reduce.jl:44 [인라인]
  [6] mapfoldl(f::typeof(identity), op::typeof(Base.add_sum), itr::String; init::Int64)
    @ Base ./reduce.jl:175 [인라인]
  [7] mapreduce(f::typeof(identity), op::typeof(Base.add_sum), itr::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:307 [인라인]
  [8] sum(f::typeof(identity), a::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:535 [인라인]
  [9] sum(a::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:564 [인라인]
 [10] 최상위 스코프
    @ REPL[12]:1
```

!!! compat "Julia 1.10"
    이 매크로는 Julia 1.10부터 사용할 수 있습니다.

