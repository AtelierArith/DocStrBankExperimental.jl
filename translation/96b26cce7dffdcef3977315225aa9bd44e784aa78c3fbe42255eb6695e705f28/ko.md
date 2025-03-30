```
if/elseif/else
```

`if`/`elseif`/`else`는 조건 평가를 수행하며, 이는 코드의 일부가 부울 표현식의 값에 따라 평가되거나 평가되지 않도록 합니다. 다음은 `if`/`elseif`/`else` 조건 구문의 구조입니다:

```julia
if x < y
    println("x는 y보다 작습니다")
elseif x > y
    println("x는 y보다 큽니다")
else
    println("x는 y와 같습니다")
end
```

조건 표현식 `x < y`가 참이면 해당 블록이 평가됩니다. 그렇지 않으면 조건 표현식 `x > y`가 평가되고, 만약 그것이 참이면 해당 블록이 평가됩니다. 두 표현식 모두 참이 아니면 `else` 블록이 평가됩니다. `elseif` 및 `else` 블록은 선택 사항이며, 원하는 만큼 많은 `elseif` 블록을 사용할 수 있습니다.

다른 일부 언어와 달리 조건은 `Bool` 유형이어야 합니다. 조건이 `Bool`로 변환 가능하다고 해서 충분하지 않습니다.

```jldoctest
julia> if 1 end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```
