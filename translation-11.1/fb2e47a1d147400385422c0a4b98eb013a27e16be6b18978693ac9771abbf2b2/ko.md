```
@invoke f(arg::T, ...; kwargs...)
```

[`invoke`](@ref)를 호출하는 편리한 방법을 제공하며, `@invoke f(arg1::T1, arg2::T2; kwargs...)`를 `invoke(f, Tuple{T1,T2}, arg1, arg2; kwargs...)`로 확장합니다. 인수의 타입 주석이 생략되면, 해당 인수의 `Core.Typeof`으로 대체됩니다. 인수가 타입이 지정되지 않았거나 명시적으로 `Any`로 지정된 메서드를 호출하려면, 인수에 `::Any`로 주석을 달아야 합니다.

다음 구문도 지원합니다:

  * `@invoke (x::X).f`는 `invoke(getproperty, Tuple{X,Symbol}, x, :f)`로 확장됩니다.
  * `@invoke (x::X).f = v::V`는 `invoke(setproperty!, Tuple{X,Symbol,V}, x, :f, v)`로 확장됩니다.
  * `@invoke (xs::Xs)[i::I]`는 `invoke(getindex, Tuple{Xs,I}, xs, i)`로 확장됩니다.
  * `@invoke (xs::Xs)[i::I] = v::V`는 `invoke(setindex!, Tuple{Xs,V,I}, xs, v, i)`로 확장됩니다.

# 예제

```jldoctest
julia> @macroexpand @invoke f(x::T, y)
:(Core.invoke(f, Tuple{T, Core.Typeof(y)}, x, y))

julia> @invoke 420::Integer % Unsigned
0x00000000000001a4

julia> @macroexpand @invoke (x::X).f
:(Core.invoke(Base.getproperty, Tuple{X, Core.Typeof(:f)}, x, :f))

julia> @macroexpand @invoke (x::X).f = v::V
:(Core.invoke(Base.setproperty!, Tuple{X, Core.Typeof(:f), V}, x, :f, v))

julia> @macroexpand @invoke (xs::Xs)[i::I]
:(Core.invoke(Base.getindex, Tuple{Xs, I}, xs, i))

julia> @macroexpand @invoke (xs::Xs)[i::I] = v::V
:(Core.invoke(Base.setindex!, Tuple{Xs, V, I}, xs, v, i))
```

!!! compat "Julia 1.7"
    이 매크로는 Julia 1.7 이상이 필요합니다.


!!! compat "Julia 1.9"
    이 매크로는 Julia 1.9부터 내보내집니다.


!!! compat "Julia 1.10"
    추가 구문은 Julia 1.10부터 지원됩니다.

