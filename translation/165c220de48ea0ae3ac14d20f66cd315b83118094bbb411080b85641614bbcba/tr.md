```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Artifacts/docs/src/index.md"
```

# Artifacts

```@meta
DocTestSetup = :(using Artifacts)
```

Julia 1.6 ile birlikte, artefakt desteği `Pkg.jl`'den Julia'nın kendisine taşındı. Buraya uygun bir belge eklenene kadar, artefaktlar hakkında daha fazla bilgi almak için `Pkg.jl` kılavuzuna [https://julialang.github.io/Pkg.jl/v1/artifacts/](https://julialang.github.io/Pkg.jl/v1/artifacts/) adresinden ulaşabilirsiniz.

!!! compat "Julia 1.6"
    Julia'nın artifacts API'si en az Julia 1.6 gerektirir. Julia sürümleri 1.3 ile 1.5 arasında, bunun yerine `Pkg.Artifacts` kullanabilirsiniz.


```@docs
Artifacts.artifact_meta
Artifacts.artifact_hash
Artifacts.find_artifacts_toml
Artifacts.@artifact_str
Artifacts.artifact_exists
Artifacts.artifact_path
Artifacts.select_downloadable_artifacts
```
