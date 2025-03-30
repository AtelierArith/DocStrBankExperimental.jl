```
@with (var::ScopedValue{T} => val)... expr
```

`with`의 매크로 버전입니다. 표현식 `@with var=>val expr`는 `var`가 `val`로 설정된 새로운 동적 범위에서 `expr`을 평가합니다. `val`은 타입 `T`로 변환됩니다. `@with var=>val expr`는 `with(var=>val) do expr end`와 동등하지만, `@with`는 클로저 생성을 피합니다.

참고: [`ScopedValues.with`](@ref), [`ScopedValues.ScopedValue`](@ref), [`ScopedValues.get`](@ref).

# 예제

```jldoctest
julia> using Base.ScopedValues

julia> const a = ScopedValue(1);

julia> f(x) = a[] + x;

julia> @with a=>2 f(10)
12

julia> @with a=>3 begin
           x = 100
           f(x)
       end
103
```
