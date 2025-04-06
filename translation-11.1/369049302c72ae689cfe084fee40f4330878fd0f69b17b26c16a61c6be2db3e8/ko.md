```
redirect_stdio(;stdin=stdin, stderr=stderr, stdout=stdout)
```

`stdin`, `stderr`, `stdout`의 하위 집합을 리디렉션합니다. 각 인수는 `IOStream`, `TTY`, [`Pipe`](@ref), 소켓 또는 `devnull`이어야 합니다.

!!! compat "Julia 1.7"
    `redirect_stdio`는 Julia 1.7 이상이 필요합니다.

