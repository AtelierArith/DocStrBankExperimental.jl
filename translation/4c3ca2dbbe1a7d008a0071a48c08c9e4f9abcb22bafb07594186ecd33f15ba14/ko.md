```
parentmodule(t::DataType) -> Module
```

정의된 (잠재적으로 `UnionAll`로 감싸진) `DataType`을 포함하는 모듈을 결정합니다.

# 예시

```jldoctest
julia> module Foo
           struct Int end
       end
Foo

julia> parentmodule(Int)
Core

julia> parentmodule(Foo.Int)
Foo
```
