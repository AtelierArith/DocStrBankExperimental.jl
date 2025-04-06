```
Base.locate_package(pkg::PkgId)::Union{String, Nothing}
```

식별자 `pkg`에 해당하는 패키지의 진입점 파일 경로 또는 찾을 수 없는 경우 `nothing`입니다. [`identify_package`](@ref)도 참조하십시오.

```julia-repl
julia> pkg = Base.identify_package("Pkg")
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> Base.locate_package(pkg)
"/path/to/julia/stdlib/v1.11/Pkg/src/Pkg.jl"
```
