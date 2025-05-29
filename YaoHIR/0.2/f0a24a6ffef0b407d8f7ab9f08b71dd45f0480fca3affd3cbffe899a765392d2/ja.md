```
GenericRoutine{name} <: Function
```

`GenericRoutine`は量子デバイス上で直接実行することはできません。これは`Operation`を返すJuliaの`Function`であり、`Operation`は量子デバイス上で実行できます。

!!! note
    `GenericRoutine`のインスタンスは`Function`のように扱うべきです。

