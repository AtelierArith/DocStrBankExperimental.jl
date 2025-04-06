# Module loading

[`Base.require`](@ref)는 모듈을 로드하는 역할을 하며, 사전 컴파일 캐시도 관리합니다. 이는 `import` 문장의 구현입니다.

## Experimental features

아래의 기능은 실험적이며 안정적인 Julia API의 일부가 아닙니다. 이들을 기반으로 작업하기 전에 현재의 생각과 곧 변경될 가능성이 있는지에 대해 정보를 확인하십시오.

### Package loading callbacks

`Base.require`에 의해 로드된 패키지를 콜백을 등록하여 들을 수 있습니다.

```julia
loaded_packages = Base.PkgId[]
callback = (pkg::Base.PkgId) -> push!(loaded_packages, pkg)
push!(Base.package_callbacks, callback)
```

이것을 사용하면 다음과 같은 모습이 될 것입니다:

```julia-repl
julia> using Example

julia> loaded_packages
1-element Vector{Base.PkgId}:
 Example [7876af07-990d-54b4-ab0e-23690620f79a]
```
