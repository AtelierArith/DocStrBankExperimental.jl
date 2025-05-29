```
ArrayReg{D,T,MT<:AbstractMatrix{T}} <: AbstractArrayRegister{D}
ArrayReg{D}(raw)
ArrayReg(raw::AbstractVecOrMat; nlevel=2)
ArrayReg(r::ArrayReg)
```

シミュレートされたフル振幅レジスタタイプで、対応する1つまたはバッチの量子状態を表すために配列を使用します。 `T`は各振幅の数値型で、デフォルトでは`ComplexF64`です。

!!! warning
    `ArrayReg`コンストラクタは量子状態を正規化しません。正規化された量子状態が必要な場合は、レジスタに対して`normalize!(register)`を使用することを忘れないでください。

