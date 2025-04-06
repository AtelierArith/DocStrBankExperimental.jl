```
pkgdir(m::Module[, paths::String...])
```

Modül `m`'yi tanımlayan paketin kök dizinini döndürür veya `m` bir pakette tanımlanmamışsa `nothing` döner. İsteğe bağlı olarak, paket kökünde bir yol oluşturmak için daha fazla yol bileşeni dizesi sağlanabilir.

Geçerli modülü uygulayan paketin kök dizinini almak için `pkgdir(@__MODULE__)` biçimi kullanılabilir.

Bir uzantı modülü verildiğinde, üst paketin kökü döndürülür.

```julia-repl
julia> pkgdir(Foo)
"/path/to/Foo.jl"

julia> pkgdir(Foo, "src", "file.jl")
"/path/to/Foo.jl/src/file.jl"
```

Ayrıca [`pathof`](@ref) bakınız.

!!! compat "Julia 1.7"
    İsteğe bağlı argüman `paths`, en az Julia 1.7'yi gerektirir.

