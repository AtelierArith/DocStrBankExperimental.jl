```
@deprecate old new [export_old=true]
```

메서드 `old`를 사용 중단하고 대체 호출 `new`를 지정하며, 이 과정에서 지정된 시그니처로 새로운 메서드 `old`를 정의합니다.

`old`가 내보내지 않도록 하려면 `export_old`를 `false`로 설정합니다.

자세한 내용은 [`Base.depwarn()`](@ref)를 참조하세요.

!!! compat "Julia 1.5"
    Julia 1.5부터 `@deprecate`로 정의된 함수는 `--depwarn=yes` 플래그 없이 `julia`를 실행할 때 경고를 출력하지 않습니다. 기본값인 `--depwarn` 옵션은 `no`입니다. 경고는 `Pkg.test()`로 실행된 테스트에서 출력됩니다.


# 예제

```jldoctest
julia> @deprecate old(x) new(x)
old (generic function with 1 method)

julia> @deprecate old(x) new(x) false
old (generic function with 1 method)
```

명시적인 타입 주석 없이 `@deprecate`를 호출하면 `Any` 타입의 위치 인수와 키워드 인수를 허용하는 사용 중단된 메서드가 정의됩니다.

!!! compat "Julia 1.9"
    Julia 1.9부터는 명시적인 타입 주석이 없을 때 키워드 인수가 전달됩니다. 이전 버전에서는 `@deprecate old(args...; kwargs...) new(args...; kwargs...)`를 사용하여 수동으로 위치 인수와 키워드 인수를 전달할 수 있습니다.


특정 시그니처로 사용 중단을 제한하려면 `old`의 인수를 주석으로 달아야 합니다. 예를 들어,

```jldoctest; filter = r"@ .*"a
julia> new(x::Int) = x;

julia> new(x::Float64) = 2x;

julia> @deprecate old(x::Int) new(x);

julia> methods(old)
# 1 method for generic function "old" from Main:
 [1] old(x::Int64)
     @ deprecated.jl:94
```

이는 `new(x::Int)`을 반영하는 `old(x::Int)`라는 메서드를 정의하고 사용 중단하지만, `old(x::Float64)` 메서드는 정의하거나 사용 중단하지 않습니다.
