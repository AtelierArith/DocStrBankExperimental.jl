```
UndefRefError()
```

주어진 객체에 대해 항목이나 필드가 정의되지 않았습니다.

# 예제

```jldoctest
julia> struct MyType
           a::Vector{Int}
           MyType() = new()
       end

julia> A = MyType()
MyType(#undef)

julia> A.a
ERROR: UndefRefError: access to undefined reference
Stacktrace:
[...]
```
