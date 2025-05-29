```
phase(theta)
```

グローバル位相ゲートを返します。次の行列形式で定義されています：

$$
e^{iθ} I
$$

### 例

位相（実数）を持つグローバル位相ゲートを作成できます。

```jldoctest; setup=:(using YaoBlocks)
julia> phase(0.1)
phase(0.1)
```
