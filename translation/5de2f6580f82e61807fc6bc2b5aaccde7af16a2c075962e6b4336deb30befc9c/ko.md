```
pathof(m::Module)
```

모듈 `m`을 `import`하는 데 사용된 `m.jl` 파일의 경로를 반환하거나, `m`이 패키지에서 가져오지 않은 경우 `nothing`을 반환합니다.

경로의 디렉토리 부분을 얻으려면 [`dirname`](@ref)를 사용하고, 파일 이름 부분을 얻으려면 [`basename`](@ref)를 사용하세요.

또한 [`pkgdir`](@ref)를 참조하세요.
