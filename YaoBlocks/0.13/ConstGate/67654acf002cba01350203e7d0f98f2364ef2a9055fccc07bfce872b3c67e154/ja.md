```
@const_gate <gate name> = <expr>
@const_gate <gate name>::<type> = <expr>
@const_gate <gate>::<type>
```

このマクロは定数ゲートの定義を簡素化します。実行時のメモリ割り当てを減らすために、行列形式を定数に自動的にバインドします。

### 例

```julia
@const_gate X = ComplexF64[0 1;1 0]
```

または

```julia
@const_gate X::ComplexF64 = [0 1;1 0]
```

新しい要素型をバインドするには、型注釈を付けて再宣言するだけです。

```julia
@const_gate X::ComplexF32
```
