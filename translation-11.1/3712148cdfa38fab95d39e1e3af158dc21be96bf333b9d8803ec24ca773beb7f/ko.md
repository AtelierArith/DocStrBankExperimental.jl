```
procs()
```

모든 프로세스 식별자 목록을 반환하며, 여기에는 pid 1도 포함됩니다(이는 [`workers()`](@ref)에서 포함되지 않음).

# 예시

```julia-repl
$ julia -p 2

julia> procs()
3-element Array{Int64,1}:
 1
 2
 3
```
