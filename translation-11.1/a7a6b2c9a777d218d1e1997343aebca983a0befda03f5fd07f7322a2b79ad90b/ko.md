```
pkgdir(m::Module[, paths::String...])
```

모듈 `m`을 선언한 패키지의 루트 디렉토리를 반환하며, `m`이 패키지에서 선언되지 않은 경우 `nothing`을 반환합니다. 선택적으로 추가 경로 구성 문자열을 제공하여 패키지 루트 내의 경로를 구성할 수 있습니다.

현재 모듈을 구현하는 패키지의 루트 디렉토리를 얻으려면 `pkgdir(@__MODULE__)` 형식을 사용할 수 있습니다.

확장 모듈이 주어지면 부모 패키지의 루트가 반환됩니다.

```julia-repl
julia> pkgdir(Foo)
"/path/to/Foo.jl"

julia> pkgdir(Foo, "src", "file.jl")
"/path/to/Foo.jl/src/file.jl"
```

자세한 내용은 [`pathof`](@ref)를 참조하세요.

!!! compat "Julia 1.7"
    선택적 인수 `paths`는 최소한 Julia 1.7이 필요합니다.

