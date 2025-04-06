```
@noinline
```

컴파일러에게 함수를 인라인하지 말라는 힌트를 제공합니다.

작은 함수는 일반적으로 자동으로 인라인됩니다. 작은 함수에 `@noinline`을 사용하면 자동 인라인을 방지할 수 있습니다.

`@noinline`은 함수 정의 바로 앞이나 함수 본문 내에서 적용할 수 있습니다.

```julia
# 긴 정의 주석 달기
@noinline function longdef(x)
    ...
end

# 짧은 정의 주석 달기
@noinline shortdef(x) = ...

# `do` 블록이 생성하는 익명 함수 주석 달기
f() do
    @noinline
    ...
end
```

!!! compat "Julia 1.8"
    함수 본문 내에서의 사용은 최소한 Julia 1.8이 필요합니다.


---

```
@noinline block
```

컴파일러에게 `block` 내의 호출을 인라인하지 말라는 힌트를 제공합니다.

```julia
# 컴파일러는 `f`를 인라인하지 않으려고 할 것입니다.
@noinline f(...)

# 컴파일러는 `f`, `g` 및 `+`를 인라인하지 않으려고 할 것입니다.
@noinline f(...) + g(...)
```

!!! note
    호출 지점 주석은 호출된 함수의 정의에 적용된 주석보다 항상 우선합니다:

    ```julia
    @inline function explicit_inline(args...)
        # 본문
    end

    let
        @noinline explicit_inline(args...) # 인라인되지 않을 것입니다.
    end
    ```


!!! note
    중첩된 호출 지점 주석이 있을 때, 가장 안쪽 주석이 우선합니다:

    ```julia
    @inline let a0, b0 = ...
        a = @noinline f(a0)  # 컴파일러는 이 호출을 인라인하지 않으려고 할 것입니다.
        b = f(b0)            # 컴파일러는 이 호출을 인라인하려고 할 것입니다.
        return a, b
    end
    ```


!!! compat "Julia 1.8"
    호출 지점 주석은 최소한 Julia 1.8이 필요합니다.


---

!!! note
    함수가 사소한 경우(예: 상수를 반환하는 경우)에는 어쨌든 인라인될 수 있습니다.

