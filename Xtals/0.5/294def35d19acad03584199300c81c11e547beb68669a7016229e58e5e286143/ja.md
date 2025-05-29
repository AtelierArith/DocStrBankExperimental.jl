```
`set_paths("path_to_data", print_paths=true)`
```

`rc[:paths]`内のすべてのパスを`path_to_data`に対して相対的に設定します。パスは`rc[:paths][:foo] = "path_to_data/foo"`の標準形式に従いますが、`rc[:paths][:data]`は`"path_to_data"`です。選択したパスが無効なフォルダーである場合は警告が発行されます。

# 引数

  * `path_to_data::AbstractString` : データフォルダーツリーのルートとして使用する絶対パスまたは相対パス。デフォルトは現在の作業ディレクトリです。
  * `print_paths::Bool` : オプション。`true`の場合、`rc[:paths]`の内容をコンソールに出力します。デフォルトは`false`です。
  * `no_warn::Bool` : オプション。無効なパスの警告を抑制するには`true`に設定します。デフォルトは`false`です。
