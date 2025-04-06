```@meta
EditURL = "https://github.com/JuliaLang/Pkg.jl/blob/master/docs/src/basedocs.md"
```

# Pkg

Pkg는 Julia의 내장 패키지 관리자이며, 패키지를 설치, 업데이트 및 제거하는 작업을 처리합니다.

!!! note
    다음은 Pkg에 대한 매우 간단한 소개입니다. `Project.toml` 파일, `Manifest.toml` 파일, 패키지 버전 호환성(`[compat]`), 환경, 레지스트리 등에 대한 더 많은 정보는 전체 매뉴얼을 읽는 것이 강력히 권장됩니다. 전체 매뉴얼은 여기에서 확인할 수 있습니다: [https://pkgdocs.julialang.org](https://pkgdocs.julialang.org).


```@eval
import Markdown
file = joinpath(Sys.STDLIB, "Pkg", "docs", "src", "getting-started.md")
str = read(file, String)
str = replace(str, r"^#.*$"m => "")
str = replace(str, "[API Reference](@ref)" => "[API Reference](https://pkgdocs.julialang.org/v1/api/)")
str = replace(str, "(@ref Working-with-Environments)" => "(https://pkgdocs.julialang.org/v1/environments/)")
str = replace(str, "(@ref Managing-Packages)" => "(https://pkgdocs.julialang.org/v1/managing-packages/)")
Markdown.parse(str)
```
