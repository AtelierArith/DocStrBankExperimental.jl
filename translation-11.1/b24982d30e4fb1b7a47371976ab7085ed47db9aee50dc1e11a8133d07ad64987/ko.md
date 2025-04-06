```
nameof(t::DataType) -> Symbol
```

주어진 (잠재적으로 `UnionAll`로 감싸진) `DataType`의 이름을 부모 모듈 없이 기호로 가져옵니다.

# 예제

```jldoctest
julia> module Foo
           struct S{T}
           end
       end
Foo

julia> nameof(Foo.S{T} where T)
:S
```
