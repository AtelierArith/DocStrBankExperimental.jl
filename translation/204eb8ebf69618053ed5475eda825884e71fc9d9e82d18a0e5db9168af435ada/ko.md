```
return
```

`return x`는 포함된 함수가 조기에 종료되도록 하여 주어진 값 `x`를 호출자에게 반환합니다. 값 없이 단독으로 사용된 `return`은 `return nothing`과 동일합니다(자세한 내용은 [`nothing`](@ref)를 참조하세요).

```julia
function compare(a, b)
    a == b && return "equal to"
    a < b ? "less than" : "greater than"
end
```

일반적으로 함수 본문 내의 어디에서나 `return` 문을 배치할 수 있으며, 깊이 중첩된 루프나 조건문 내에서도 사용할 수 있지만, `do` 블록에서는 주의해야 합니다. 예를 들어:

```julia
function test1(xs)
    for x in xs
        iseven(x) && return 2x
    end
end

function test2(xs)
    map(xs) do x
        iseven(x) && return 2x
        x
    end
end
```

첫 번째 예제에서 `return`은 짝수에 도달하자마자 `test1`을 종료하므로, `test1([5,6,7])`은 `12`를 반환합니다.

두 번째 예제가 같은 방식으로 작동할 것이라고 예상할 수 있지만, 사실 `return`은 *내부* 함수(즉, `do` 블록 내)에서만 종료되고 `map`에 값을 반환합니다. 따라서 `test2([5,6,7])`는 `[5,12,7]`을 반환합니다.

최상위 표현식(즉, 어떤 함수 외부)에서 사용될 때, `return`은 현재의 전체 최상위 표현식을 조기에 종료시킵니다.
