```
fieldtype(T, name::Symbol | index::Int)
```

합성 데이터 타입 `T`에서 필드(이름 또는 인덱스로 지정)의 선언된 타입을 결정합니다.

# 예제

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtype(Foo, :x)
Int64

julia> fieldtype(Foo, 2)
String
```
