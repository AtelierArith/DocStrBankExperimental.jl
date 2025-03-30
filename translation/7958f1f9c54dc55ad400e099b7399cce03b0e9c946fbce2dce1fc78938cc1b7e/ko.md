```
ℯ
e
```

상수 ℯ.

유니코드 `ℯ`는 Julia REPL에서 `\euler`를 입력하고 탭을 눌러 입력할 수 있으며, 많은 편집기에서도 가능합니다.

참고: [`exp`](@ref), [`cis`](@ref), [`cispi`](@ref).

# 예제

```jldoctest
julia> ℯ
ℯ = 2.7182818284590...

julia> log(ℯ)
1

julia> ℯ^(im)π ≈ -1
true
```
