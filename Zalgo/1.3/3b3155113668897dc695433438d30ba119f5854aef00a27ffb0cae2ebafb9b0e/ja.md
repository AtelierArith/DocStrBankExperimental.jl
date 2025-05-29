```
script(str; roundhand=false)
```

文字列 `str` のバージョンを、Unicode テーブルからの数学的スクリプト文字で返します。

数学的スクリプト文字には、基本的に2つのスタイルがあります： “通常の” カリグラフィックまたはシャンセリーアルファベットと、“ファンシースクリプト” またはラウンドハンドアルファベットです。

デフォルトでは、スクリプトスタイルは “script” になります。`roundhand` が true の場合、スタイルは “roundhand” になります。

詳細については、[このUnicode文書](https://www.unicode.org/L2/L2020/20275r-math-calligraphic.pdf)を参照してください。
