```
relpath(path::AbstractString, startpath::AbstractString = ".") -> String
```

`path`に対する相対ファイルパスを、現在のディレクトリまたはオプションの開始ディレクトリから返します。これはパス計算です：`path`や`startpath`の存在や性質を確認するためにファイルシステムにはアクセスしません。

Windowsでは、ドライブレターを除くパスのすべての部分に対して大文字小文字の区別が適用されます。`path`と`startpath`が異なるドライブを指す場合、`path`の絶対パスが返されます。
