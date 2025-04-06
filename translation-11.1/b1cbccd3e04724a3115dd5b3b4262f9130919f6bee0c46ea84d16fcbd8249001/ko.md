```
getglobal(module::Module, name::Symbol, [order::Symbol=:monotonic])
```

모듈 `module`에서 바인딩 `name`의 값을 검색합니다. 선택적으로, 작업에 대한 원자적 순서를 정의할 수 있으며, 그렇지 않으면 기본값은 단조(monotonic)입니다.

[`getfield`](@ref)를 사용하여 모듈 바인딩에 접근하는 것은 호환성을 유지하기 위해 여전히 지원되지만, `getglobal`을 사용하는 것이 항상 선호되어야 합니다. `getglobal`은 원자적 순서에 대한 제어를 허용하며(`getfield`는 항상 단조입니다), 사용자와 컴파일러 모두에게 코드의 의도를 더 잘 나타냅니다.

대부분의 사용자는 이 함수를 직접 호출할 필요가 없습니다 – [`getproperty`](@ref Base.getproperty) 함수나 해당 구문(즉, `module.name`)이 매우 특정한 사용 사례를 제외하고는 항상 선호되어야 합니다.

!!! compat "Julia 1.9"
    이 함수는 Julia 1.9 이상이 필요합니다.


또한 [`getproperty`](@ref Base.getproperty) 및 [`setglobal!`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> a = 1
1

julia> module M
       a = 2
       end;

julia> getglobal(@__MODULE__, :a)
1

julia> getglobal(M, :a)
2
```
