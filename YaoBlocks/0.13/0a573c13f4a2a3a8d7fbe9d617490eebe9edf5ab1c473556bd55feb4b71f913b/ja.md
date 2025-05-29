```julia
struct Projector{D, T, AT<:(YaoArrayRegister.AbstractArrayReg{D, T})} <: YaoAPI.PrimitiveBlock{D}
```

状態 `psi` をターゲットとする射影演算子。

### 定義

`projector(s)` は次の演算子を定義します。

$$
|s⟩ → |s⟩⟨s|
$$
