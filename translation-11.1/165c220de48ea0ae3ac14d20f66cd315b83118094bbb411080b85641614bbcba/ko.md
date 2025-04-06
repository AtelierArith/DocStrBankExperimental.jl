```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Artifacts/docs/src/index.md"
```

# Artifacts

```@meta
DocTestSetup = :(using Artifacts)
```

Julia 1.6부터 아티팩트 지원이 `Pkg.jl`에서 Julia 자체로 이동했습니다. 여기에서 적절한 문서를 추가할 수 있을 때까지, `Pkg.jl` 매뉴얼에서 아티팩트에 대해 더 알아보실 수 있습니다: [https://julialang.github.io/Pkg.jl/v1/artifacts/](https://julialang.github.io/Pkg.jl/v1/artifacts/).

!!! compat "Julia 1.6"
    줄리아의 아티팩트 API는 최소한 줄리아 1.6이 필요합니다. 줄리아 버전 1.3에서 1.5까지는 대신 `Pkg.Artifacts`를 사용할 수 있습니다.


```@docs
Artifacts.artifact_meta
Artifacts.artifact_hash
Artifacts.find_artifacts_toml
Artifacts.@artifact_str
Artifacts.artifact_exists
Artifacts.artifact_path
Artifacts.select_downloadable_artifacts
```
