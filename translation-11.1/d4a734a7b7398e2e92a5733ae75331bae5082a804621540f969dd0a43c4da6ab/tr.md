```
Base.locate_package(pkg::PkgId)::Union{String, Nothing}
```

Belirtilen `pkg` tanımlayıcısına karşılık gelen paketin giriş noktası dosyasının yolu veya bulunamazsa `nothing`. Ayrıca bkz. [`identify_package`](@ref).

```julia-repl
julia> pkg = Base.identify_package("Pkg")
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> Base.locate_package(pkg)
"/path/to/julia/stdlib/v1.11/Pkg/src/Pkg.jl"
```
