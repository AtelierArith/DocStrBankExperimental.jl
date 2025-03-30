```
lowrankupdowndate!(F::CHOLMOD.Factor, C::Sparse, update::Cint)
```

`A`의 `LDLt` 또는 `LLt` 분해 `F`를 `A ± C*C'`의 분해로 업데이트합니다.

희소성을 유지하는 분해가 사용되는 경우, 즉 `L*L' == P*A*P'`이면 새로운 분해는 `L*L' == P*A*P' + C'*C`가 됩니다.

`update`: `Cint(1)`은 `A + CC'`에 대한 것이고, `Cint(0)`은 `A - CC'`에 대한 것입니다.
