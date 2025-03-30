```
acquire(f, s::Semaphore)
```

세마포어 `s`에서 획득한 후 `f`를 실행하고, 완료 또는 오류 시 `release`합니다.

예를 들어, 동시에 `foo`가 2번만 활성화되도록 보장하는 do-block 형태:

```julia
s = Base.Semaphore(2)
@sync for _ in 1:100
    Threads.@spawn begin
        Base.acquire(s) do
            foo()
        end
    end
end
```

!!! compat "Julia 1.8"
    이 메서드는 최소한 Julia 1.8이 필요합니다.

