```
readdir(dir::AbstractString=pwd();
    join::Bool = false,
    sort::Bool = true,
) -> Vector{String}
```

`dir` dizinindeki isimleri veya verilmediği takdirde mevcut çalışma dizinindeki isimleri döndürür. `join` false olduğunda, `readdir` dizindeki isimleri olduğu gibi döndürür; `join` true olduğunda ise her `name` için `joinpath(dir, name)` döndürerek, döndürülen dizelerin tam yollarını sağlar. Mutlak yollar almak istiyorsanız, `readdir`'i mutlak bir dizin yolu ve `join` true olarak çağırmalısınız.

Varsayılan olarak, `readdir` döndürdüğü isimlerin listesini sıralar. İsimleri sıralamadan atlamak ve dosya sisteminin listelediği sırayla almak istiyorsanız, sıralamadan vazgeçmek için `readdir(dir, sort=false)` kullanabilirsiniz.

Ayrıca bakınız: [`walkdir`](@ref).

!!! compat "Julia 1.4"
    `join` ve `sort` anahtar argümanları en az Julia 1.4 gerektirir.


# Örnekler

```julia-repl
julia> cd("/home/JuliaUser/dev/julia")

julia> readdir()
30-element Array{String,1}:
 ".appveyor.yml"
 ".git"
 ".gitattributes"
 ⋮
 "ui"
 "usr"
 "usr-staging"

julia> readdir(join=true)
30-element Array{String,1}:
 "/home/JuliaUser/dev/julia/.appveyor.yml"
 "/home/JuliaUser/dev/julia/.git"
 "/home/JuliaUser/dev/julia/.gitattributes"
 ⋮
 "/home/JuliaUser/dev/julia/ui"
 "/home/JuliaUser/dev/julia/usr"
 "/home/JuliaUser/dev/julia/usr-staging"

julia> readdir("base")
145-element Array{String,1}:
 ".gitignore"
 "Base.jl"
 "Enums.jl"
 ⋮
 "version_git.sh"
 "views.jl"
 "weakkeydict.jl"

julia> readdir("base", join=true)
145-element Array{String,1}:
 "base/.gitignore"
 "base/Base.jl"
 "base/Enums.jl"
 ⋮
 "base/version_git.sh"
 "base/views.jl"
 "base/weakkeydict.jl"

julia> readdir(abspath("base"), join=true)
145-element Array{String,1}:
 "/home/JuliaUser/dev/julia/base/.gitignore"
 "/home/JuliaUser/dev/julia/base/Base.jl"
 "/home/JuliaUser/dev/julia/base/Enums.jl"
 ⋮
 "/home/JuliaUser/dev/julia/base/version_git.sh"
 "/home/JuliaUser/dev/julia/base/views.jl"
 "/home/JuliaUser/dev/julia/base/weakkeydict.jl"
```
