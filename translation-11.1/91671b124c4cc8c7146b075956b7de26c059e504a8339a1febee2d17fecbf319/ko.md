```
@spawn expr
```

표현식 주위에 클로저를 생성하고 자동으로 선택된 프로세스에서 실행하여 결과에 대한 [`Future`](@ref)를 반환합니다. 이 매크로는 더 이상 사용되지 않으며, 대신 `@spawnat :any expr`를 사용해야 합니다.

# 예제

```julia-repl
julia> addprocs(3);

julia> f = @spawn myid()
Future(2, 1, 5, nothing)

julia> fetch(f)
2

julia> f = @spawn myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    Julia 1.3부터 이 매크로는 더 이상 사용되지 않습니다. 대신 `@spawnat :any`를 사용하세요.

