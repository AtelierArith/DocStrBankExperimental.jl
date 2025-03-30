```
Meta.show_sexpr([io::IO,], ex)
```

표현식 `ex`를 lisp 스타일 S-표현식으로 표시합니다.

# 예제

```jldoctest
julia> Meta.show_sexpr(:(f(x, g(y,z))))
(:call, :f, :x, (:call, :g, :y, :z))
```
