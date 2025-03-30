```
@fetch expr
```

`fetch(@spawnat :any expr)`와 동일합니다. [`fetch`](@ref) 및 [`@spawnat`](@ref)를 참조하십시오.

# 예제

```julia-repl
julia> addprocs(3);

julia> @fetch myid()
2

julia> @fetch myid()
3

julia> @fetch myid()
4

julia> @fetch myid()
2
```
