```
splat(f)
```

동일한 의미는

```julia
    my_splat(f) = args->f(args...)
```

즉, 주어진 함수를 원래 함수에 스플랫하는 하나의 인수를 받는 새로운 함수를 반환합니다. 이는 다중 인수 함수를 단일 인수를 기대하는 컨텍스트에 전달하기 위한 어댑터로 유용하지만, 그 단일 인수로 튜플을 전달합니다.

# 예제

```jldoctest
julia> map(splat(+), zip(1:3,4:6))
3-element Vector{Int64}:
 5
 7
 9

julia> my_add = splat(+)
splat(+)

julia> my_add((1,2,3))
6
```
