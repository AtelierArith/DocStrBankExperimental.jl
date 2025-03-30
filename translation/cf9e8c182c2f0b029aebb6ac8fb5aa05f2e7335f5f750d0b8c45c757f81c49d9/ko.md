```
setglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

모듈 `module`에서 바인딩 `name`의 값을 `x`로 설정하거나 변경합니다. 타입 변환은 수행되지 않으므로, 바인딩에 대해 이미 타입이 선언된 경우 `x`는 적절한 타입이어야 하며, 그렇지 않으면 오류가 발생합니다.

또한, 이 작업에 대해 원자적 순서를 지정할 수 있으며, 그렇지 않으면 기본값은 단조(monotonic)입니다.

사용자는 일반적으로 [`setproperty!`](@ref Base.setproperty!) 함수나 해당 구문(즉, `module.name = x`)을 통해 이 기능에 접근하므로, 이는 매우 특정한 사용 사례를 위한 것입니다.

!!! compat "Julia 1.9"
    이 함수는 Julia 1.9 이상이 필요합니다.


또한 [`setproperty!`](@ref Base.setproperty!) 및 [`getglobal`](@ref)를 참조하십시오.

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> module M; global a; end;

julia> M.a  # `getglobal(M, :a)`와 동일
ERROR: UndefVarError: `a` not defined in `M`
제안: 적절한 import 또는 할당을 추가하십시오. 이 전역은 선언되었지만 할당되지 않았습니다.
Stacktrace:
 [1] getproperty(x::Module, f::Symbol)
   @ Base ./Base.jl:42
 [2] top-level scope
   @ none:1

julia> setglobal!(M, :a, 1)
1

julia> M.a
1
```
