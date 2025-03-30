```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Artifacts/docs/src/index.md"
```

# Artifacts

```@meta
DocTestSetup = :(using Artifacts)
```

从 Julia 1.6 开始，工件支持已从 `Pkg.jl` 移至 Julia 本身。在这里添加适当文档之前，您可以在 `Pkg.jl` 手册中了解有关工件的更多信息，网址为 [https://julialang.github.io/Pkg.jl/v1/artifacts/](https://julialang.github.io/Pkg.jl/v1/artifacts/)。

!!! compat "Julia 1.6"
    Julia 的 artifacts API 至少需要 Julia 1.6。在 Julia 1.3 到 1.5 版本中，您可以使用 `Pkg.Artifacts`。


```@docs
Artifacts.artifact_meta
Artifacts.artifact_hash
Artifacts.find_artifacts_toml
Artifacts.@artifact_str
Artifacts.artifact_exists
Artifacts.artifact_path
Artifacts.select_downloadable_artifacts
```
