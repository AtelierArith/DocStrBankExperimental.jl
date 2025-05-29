```
ReflectGate{D, T, Tt, AT<:AbstractArrayReg{D, T}} = TimeEvolution{D,Tt,Projector{D,T,AT}}
```

量子状態ベクトルを `|v⟩` とすると、反射ゲートは次の操作として定義されるユニタリ演算子です。

$$
|v⟩ → 1 - (1-exp(-iθ)) |v⟩⟨v|
$$

$$
θ = π
$$

のとき、標準の反射ゲート $1-2|v⟩⟨v|$ を定義します。
