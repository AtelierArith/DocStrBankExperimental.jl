zcreate(T, dims...;kwargs)

新しい空のzarr配列を要素タイプ`T`と配列次元`dims`で作成します。次のキーワード引数が受け入れられます：

  * `path=""` 永続的な配列を保存するディレクトリ名。空のままにすると、メモリ内配列が作成されます
  * `name=""` zarr配列の名前、デフォルトはディレクトリ名
  * `storagetype` 使用するストレージを決定します。現在のオプションは`DirectoryStore`または`DictStore`
  * `chunks=dims` 個々の配列チャンクのサイズ、`length(dims)`の長さのタプルでなければなりません
  * `fill_value=nothing` 欠損値を表す値
  * `fill_as_missing=false` `true`に設定すると、fillvalueが`missing`に変換されます
  * `filters` 適用されるフィルター
  * `compressor=BloscCompressor()` 圧縮タイプとプロパティ
  * `attrs=Dict()` 配列に関連付けられたメタデータ属性のキーと値のペアを含む辞書
  * `writeable=true` 配列が読み取り専用または書き込みモードで開かれているかどうかを決定します
