```
@nexprs N expr
```

`N` 개의 표현식을 생성합니다. `expr`은 익명 함수 표현식이어야 합니다.

# 예시

```jldoctest
julia> @macroexpand Base.Cartesian.@nexprs 4 i -> y[i] = A[i+j]
quote
    y[1] = A[1 + j]
    y[2] = A[2 + j]
    y[3] = A[3 + j]
    y[4] = A[4 + j]
end
```
