```
normpath(path::AbstractString, paths::AbstractString...) -> String
```

一連のパスを正規化されたパスに変換し、それらを結合して "." および ".." エントリを削除します。これは `normpath(joinpath(path, paths...))` と同等です。
