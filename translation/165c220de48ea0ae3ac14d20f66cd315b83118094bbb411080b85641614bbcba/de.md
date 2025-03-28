```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Artifacts/docs/src/index.md"
```

# Artifacts

```@meta
DocTestSetup = :(using Artifacts)
```

Ab Julia 1.6 wurde die Unterstützung für Artefakte von `Pkg.jl` in Julia selbst verschoben. Bis eine ordnungsgemäße Dokumentation hier hinzugefügt werden kann, können Sie mehr über Artefakte im `Pkg.jl`-Handbuch unter [https://julialang.github.io/Pkg.jl/v1/artifacts/](https://julialang.github.io/Pkg.jl/v1/artifacts/) erfahren.

!!! compat "Julia 1.6"
    Julias Artefakte-API erfordert mindestens Julia 1.6. In den Julia-Versionen 1.3 bis 1.5 können Sie stattdessen `Pkg.Artifacts` verwenden.


```@docs
Artifacts.artifact_meta
Artifacts.artifact_hash
Artifacts.find_artifacts_toml
Artifacts.@artifact_str
Artifacts.artifact_exists
Artifacts.artifact_path
Artifacts.select_downloadable_artifacts
```
