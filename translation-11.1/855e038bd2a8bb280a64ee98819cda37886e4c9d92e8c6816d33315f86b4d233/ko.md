```
@fetchfrom
```

`fetch(@spawnat p expr)`와 동일합니다. [`fetch`](@ref) 및 [`@spawnat`](@ref)를 참조하십시오.

# 예제

```julia-repl
julia> addprocs(3);

julia> @fetchfrom 2 myid()
2

julia> @fetchfrom 4 myid()
4
```
