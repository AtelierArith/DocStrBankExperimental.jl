```
Base.datatype_haspadding(dt::DataType) -> Bool
```

この型のインスタンスのフィールドがメモリ内でパッキングされているかどうかを返します。すなわち、構造体のフィールドに適用されたときに等価テストに唯一影響を与えないビット（パディングビットと定義される）が介在しないことを意味します。`isconcretetype`に対して呼び出すことができます。
