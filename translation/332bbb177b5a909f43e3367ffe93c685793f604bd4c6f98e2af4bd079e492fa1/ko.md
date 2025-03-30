```
nworkers()
```

사용 가능한 작업자 프로세스의 수를 가져옵니다. 이는 [`nprocs()`](@ref)보다 하나 적습니다. `nprocs() == 1`인 경우 `nprocs()`와 같습니다.

# 예제

```julia-repl
$ julia -p 2

julia> nprocs()
3

julia> nworkers()
2
```
