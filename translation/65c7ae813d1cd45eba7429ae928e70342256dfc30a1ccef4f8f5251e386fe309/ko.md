```
@ncallkw N f kw sym...
```

키워드 인수 `kw...`를 사용하여 함수 호출 표현식을 생성합니다. [`@ncall`](@ref)와 마찬가지로 `sym`은 익명 함수 표현식일 수 있는 여러 개의 함수 인수를 나타내며, `N`개의 인수로 확장됩니다.

# 예제

```jldoctest
julia> using Base.Cartesian

julia> f(x...; a, b = 1, c = 2, d = 3) = +(x..., a, b, c, d);

julia> x_1, x_2 = (-1, -2); b = 0; kw = (c = 0, d = 0);

julia> @ncallkw 2 f (; a = 0, b, kw...) x
-3

```
