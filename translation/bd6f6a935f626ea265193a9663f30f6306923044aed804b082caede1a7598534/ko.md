```
lowrankupdate!(F::CHOLMOD.Factor, C::AbstractArray)
```

`A`의 `LDLt` 또는 `LLt` 분해 `F`를 `A + C*C'`의 분해로 업데이트합니다.

`LLt` 분해는 `LDLt`로 변환됩니다.

자세한 내용은 [`lowrankupdate`](@ref), [`lowrankdowndate`](@ref), [`lowrankdowndate!`](@ref)를 참조하세요.
