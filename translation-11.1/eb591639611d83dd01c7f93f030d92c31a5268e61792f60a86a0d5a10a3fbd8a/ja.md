```
trsen!(job, compq, select, T, Q) -> (T, Q, w, s, sep)
trsen!(select, T, Q) -> (T, Q, w, s, sep)
```

行列のシュール分解を再順序付けし、オプションで逆条件数を求めます。`job = N` の場合、条件数は求められません。`job = E` の場合、この固有値のクラスターの条件数のみが求められます。`job = V` の場合、不変部分空間の条件数のみが求められます。`job = B` の場合、クラスターと部分空間の条件数が求められます。`compq = V` の場合、シュールベクトル `Q` が更新されます。`compq = N` の場合、シュールベクトルは変更されません。`select` はどの固有値がクラスターに含まれるかを決定します。3引数メソッドは、`job = N` および `compq = V` の5引数メソッドを呼び出します。

`T`、`Q`、再順序付けされた固有値 `w`、固有値のクラスターの条件数 `s`、および不変部分空間の条件数 `sep` を返します。
