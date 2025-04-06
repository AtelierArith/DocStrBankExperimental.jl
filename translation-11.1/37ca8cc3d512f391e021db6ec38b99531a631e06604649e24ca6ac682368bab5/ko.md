```
Base.identify_package(name::String)::Union{PkgId, Nothing}
Base.identify_package(where::Union{Module,PkgId}, name::String)::Union{PkgId, Nothing}
```

현재 환경 스택에서 이름으로 패키지를 식별하고, `PkgId`를 반환하거나 찾을 수 없는 경우 `nothing`을 반환합니다.

`name` 인수만 제공되는 경우, 스택의 각 환경과 그 이름이 지정된 직접 종속성을 검색합니다.

`where` 인수는 패키지를 검색할 컨텍스트를 제공합니다: 이 경우 이름이 컨텍스트 자체와 일치하는지 먼저 확인하고, 그렇지 않으면 모든 재귀 종속성을 검색합니다(각 환경의 해결된 매니페스트에서) 컨텍스트 `where`를 찾을 때까지, 그리고 거기서 해당 이름으로 종속성을 식별합니다.

```julia-repl
julia> Base.identify_package("Pkg") # Pkg는 기본 환경의 종속성입니다.
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> using LinearAlgebra

julia> Base.identify_package(LinearAlgebra, "Pkg") # Pkg는 LinearAlgebra의 종속성이 아닙니다.
```
