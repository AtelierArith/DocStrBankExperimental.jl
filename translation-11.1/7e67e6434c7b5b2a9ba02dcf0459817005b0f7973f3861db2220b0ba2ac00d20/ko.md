```
Pair(x, y)
x => y
```

`Pair` 객체를 `Pair{typeof(x), typeof(y)}` 타입으로 생성합니다. 요소는 `first`와 `second` 필드에 저장됩니다. 또한 반복을 통해 접근할 수 있습니다(하지만 `Pair`는 브로드캐스팅 작업에 대해 단일 "스칼라"로 취급됩니다).

자세한 내용은 [`Dict`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> p = "foo" => 7
"foo" => 7

julia> typeof(p)
Pair{String, Int64}

julia> p.first
"foo"

julia> for x in p
           println(x)
       end
foo
7

julia> replace.(["xops", "oxps"], "x" => "o")
2-element Vector{String}:
 "oops"
 "oops"
```
