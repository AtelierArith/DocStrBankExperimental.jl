```julia
isseparable(
    reg::YaoArrayRegister.AbstractArrayReg{D},
    locs
) -> Any

```

`locs`のquditが残りのquditから分離可能であればtrueを返します。状態$|ψ⟩$は以下のように分離可能です。

$$
|\psi\rangle = |a\rangle \otimes |b\rangle
$$

ここで、$|a⟩$は`locs`の状態空間で定義されています。

### 例

```jldoctest; setup=:(using YaoArrayRegister)
julia> isseparable(product_state(bit"01100"), 1:2)
true

julia> isseparable(ghz_state(5), 1:2)
false
```
