```
SimpleLogger([stream,] min_level=Info)
```

すべてのメッセージを `min_level` 以上のレベルで `stream` にログするためのシンプルなロガーです。ストリームが閉じている場合、ログレベルが `Warn` 以上のメッセージは `stderr` に記録され、それ以下は `stdout` に記録されます。
