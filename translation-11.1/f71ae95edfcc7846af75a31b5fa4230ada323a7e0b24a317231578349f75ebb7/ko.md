```
lowrankdowndate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

주어진 `A`의 `LDLt` 또는 `LLt` 분해 `F`에 대해 `A + C*C'`의 `LDLt` 분해를 가져옵니다.

반환된 분해는 항상 `LDLt` 분해입니다.

또한 [`lowrankdowndate!`](@ref), [`lowrankupdate`](@ref), [`lowrankupdate!`](@ref)를 참조하십시오.
