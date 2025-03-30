```
@spawnat p expr
```

표현식 주위에 클로저를 생성하고 프로세스 `p`에서 비동기적으로 클로저를 실행합니다. 결과에 대한 [`Future`](@ref)를 반환합니다. `p`가 인용된 리터럴 기호 `:any`인 경우, 시스템은 자동으로 사용할 프로세서를 선택합니다.

# 예제

```julia-repl
julia> addprocs(3);

julia> f = @spawnat 2 myid()
Future(2, 1, 3, nothing)

julia> fetch(f)
2

julia> f = @spawnat :any myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    `:any` 인자는 Julia 1.3부터 사용할 수 있습니다.

