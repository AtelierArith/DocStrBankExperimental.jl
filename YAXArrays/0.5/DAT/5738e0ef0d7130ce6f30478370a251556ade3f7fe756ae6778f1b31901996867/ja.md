```
mapCube(fun, cube, addargs...;kwargs...)
```

与えられた関数 `fun` をデータキューブ `cube` のスライスに適用します。追加の引数 `addargs` は内部関数 `fun` に転送されます。入力次元を記述するには InDims を、出力次元を記述するには OutDims を使用します。

### キーワード引数

  * `max_cache=YAXDefaults.max_cache` Float64 最大サイズのブロックがメモリに読み込まれるビット数 e.g. `max_cache=5.0e8`。または文字列。e.g. `max_cache="10MB"` または `max_cache=1GB` ``` デフォルトは約 10Mb です。
  * `indims::InDims` 各入力データキューブのための型 [`InDims`](@ref) の入力キューブ記述子のリスト。
  * `outdims::OutDims` 各出力キューブのための型 [`OutDims`](@ref) の出力キューブ記述子のリスト。
  * `inplace` 関数が出力配列にインプレースで書き込むか、単一の値を返すか> デフォルトは `true`
  * `ispar` 並列処理を適用するかどうかを決定するブール値、ワーカーが利用可能な場合はデフォルトで `true`。
  * `showprog` プログレスメーターを表示するかどうかを示すブール値
  * `include_loopvars` ループされた変数を関数引数として追加するかどうかを示すブール値
  * `nthreads` 計算のためのスレッド数、各ワーカーのためのデフォルトは Threads.nthreads。
  * `loopchunksize` ループされた変数のチャンクサイズを決定する辞書
  * `kwargs` 追加のキーワード引数は内部関数に渡されます

最初の引数は常に適用される関数であり、2番目は入力キューブまたは必要に応じて入力キューブのタプルです。
