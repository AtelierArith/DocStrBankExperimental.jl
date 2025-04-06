```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Artifacts/docs/src/index.md"
```

# Artifacts

```@meta
DocTestSetup = :(using Artifacts)
```

A partir de Julia 1.6, el soporte para artefactos se ha trasladado de `Pkg.jl` a Julia misma. Hasta que se pueda agregar la documentación adecuada aquí, puedes aprender más sobre artefactos en el manual de `Pkg.jl` en [https://julialang.github.io/Pkg.jl/v1/artifacts/](https://julialang.github.io/Pkg.jl/v1/artifacts/).

!!! compat "Julia 1.6"
    La API de artefactos de Julia requiere al menos Julia 1.6. En las versiones de Julia 1.3 a 1.5, puedes usar `Pkg.Artifacts` en su lugar.


```@docs
Artifacts.artifact_meta
Artifacts.artifact_hash
Artifacts.find_artifacts_toml
Artifacts.@artifact_str
Artifacts.artifact_exists
Artifacts.artifact_path
Artifacts.select_downloadable_artifacts
```
