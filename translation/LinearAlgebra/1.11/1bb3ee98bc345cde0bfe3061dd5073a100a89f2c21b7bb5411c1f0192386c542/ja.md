```
iszerodefined(T::Type)
```

`T` 型のオブジェクトに対して `iszero` が適切に定義されているかどうかを示す `Bool` を返します。デフォルトでは、この関数は `T <: Number` でない限り `false` を返します。`zero(::T)` が定義されていなくても、`iszero(::T)` に `zero(::T)` を必要としないメソッドがある限り、`true` を返すことに注意してください。

この関数は、特定の構造を持つ非ゼロ要素の配列の要素をマッピングする際に、この構造が保持されるかどうかを判断するために使用されます。たとえば、`tuple.(Diagonal([1, 2]))` の出力が `Diagonal([(1,), (2,)])` であるか、`[(1,) (0,); (0,) (2,)]` であるかを判断するために使用されます。このためには、`(0,)` がゼロと見なされるかどうかを判断する必要があります。`iszero((0,))` は `(0,) == zero((0,))` にフォールバックしますが、`zero(::Tuple{Int})` は定義されていないため失敗します。しかし、`iszerodefined(::Tuple{Int})` は `false` であるため、比較 `(0,) == 0` にフォールバックし、これは `false` を返し、正しい出力が `[(1,) (0,); (0,) (2,)]` であると判断します。
