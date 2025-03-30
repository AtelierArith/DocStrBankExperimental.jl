```
@inline
```

컴파일러에게 이 함수가 인라인으로 처리될 가치가 있음을 힌트합니다.

작은 함수는 일반적으로 `@inline` 주석이 필요하지 않으며, 컴파일러가 자동으로 처리합니다. 더 큰 함수에 `@inline`을 사용하면 컴파일러에게 인라인으로 처리하도록 추가적인 자극을 줄 수 있습니다.

`@inline`은 함수 정의 바로 앞이나 함수 본문 내에서 적용할 수 있습니다.

```julia
# 긴 정의에 주석 추가
@inline function longdef(x)
    ...
end

# 짧은 정의에 주석 추가
@inline shortdef(x) = ...

# `do` 블록이 생성하는 익명 함수에 주석 추가
f() do
    @inline
    ...
end
```

!!! compat "Julia 1.8"
    함수 본문 내에서의 사용은 최소한 Julia 1.8이 필요합니다.


---

```
@inline block
```

`block` 내의 호출이 인라인으로 처리될 가치가 있음을 컴파일러에게 힌트합니다.

```julia
# 컴파일러는 `f`를 인라인으로 처리하려고 시도할 것입니다.
@inline f(...)

# 컴파일러는 `f`, `g` 및 `+`를 인라인으로 처리하려고 시도할 것입니다.
@inline f(...) + g(...)
```

!!! note
    호출 지점 주석은 호출된 함수의 정의에 적용된 주석보다 항상 우선합니다:

    ```julia
    @noinline function explicit_noinline(args...)
        # 본문
    end

    let
        @inline explicit_noinline(args...) # 인라인으로 처리될 것입니다.
    end
    ```


!!! note
    중첩된 호출 지점 주석이 있을 때, 가장 안쪽 주석이 우선합니다:

    ```julia
    @noinline let a0, b0 = ...
        a = @inline f(a0)  # 컴파일러는 이 호출을 인라인으로 처리하려고 시도할 것입니다.
        b = f(b0)          # 컴파일러는 이 호출을 인라인으로 처리하지 않을 것입니다.
        return a, b
    end
    ```


!!! warning
    호출 지점 주석이 비용 모델에 관계없이 인라인 처리를 강제하려고 시도하지만, 여전히 성공하지 못할 가능성이 있습니다. 특히, 재귀 호출은 `@inline`으로 주석이 달려 있어도 인라인으로 처리될 수 없습니다.


!!! compat "Julia 1.8"
    호출 지점 주석은 최소한 Julia 1.8이 필요합니다.

