```
abspath(path::AbstractString, paths::AbstractString...) -> String
```

一連のパスを結合して絶対パスに変換し、必要に応じて現在のディレクトリを追加します。`abspath(joinpath(path, paths...))`と同等です。
