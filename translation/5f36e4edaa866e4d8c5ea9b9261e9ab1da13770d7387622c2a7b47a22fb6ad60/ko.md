```
nfields(x) -> Int
```

주어진 객체의 필드 수를 가져옵니다.

# 예제

```jldoctest
julia> a = 1//2;

julia> nfields(a)
2

julia> b = 1
1

julia> nfields(b)
0

julia> ex = ErrorException("I've done a bad thing");

julia> nfields(ex)
1
```

이 예제에서 `a`는 두 개의 필드를 가진 [`Rational`](@ref)입니다. `b`는 필드가 전혀 없는 원시 비트 타입인 `Int`입니다. `ex`는 하나의 필드를 가진 [`ErrorException`](@ref)입니다.
