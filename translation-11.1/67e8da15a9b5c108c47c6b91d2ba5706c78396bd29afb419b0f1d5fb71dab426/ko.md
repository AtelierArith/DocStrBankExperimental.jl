```
myid()
```

현재 프로세스의 ID를 가져옵니다.

# 예제

```julia-repl
julia> myid()
1

julia> remotecall_fetch(() -> myid(), 4)
4
```
