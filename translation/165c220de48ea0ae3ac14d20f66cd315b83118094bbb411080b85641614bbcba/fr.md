```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Artifacts/docs/src/index.md"
```

# Artifacts

```@meta
DocTestSetup = :(using Artifacts)
```

À partir de Julia 1.6, le support des artefacts a été déplacé de `Pkg.jl` vers Julia elle-même. En attendant que la documentation appropriée puisse être ajoutée ici, vous pouvez en apprendre davantage sur les artefacts dans le manuel de `Pkg.jl` à [https://julialang.github.io/Pkg.jl/v1/artifacts/](https://julialang.github.io/Pkg.jl/v1/artifacts/).

!!! compat "Julia 1.6"
    L'API des artefacts de Julia nécessite au moins Julia 1.6. Dans les versions de Julia 1.3 à 1.5, vous pouvez utiliser `Pkg.Artifacts` à la place.


```@docs
Artifacts.artifact_meta
Artifacts.artifact_hash
Artifacts.find_artifacts_toml
Artifacts.@artifact_str
Artifacts.artifact_exists
Artifacts.artifact_path
Artifacts.select_downloadable_artifacts
```
