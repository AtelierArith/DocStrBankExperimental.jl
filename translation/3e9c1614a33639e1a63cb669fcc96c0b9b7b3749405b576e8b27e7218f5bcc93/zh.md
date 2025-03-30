```
TextDisplay(io::IO)
```

返回一个 `TextDisplay <: AbstractDisplay`，它将任何对象显示为 text/plain MIME 类型（默认情况下），并将文本表示写入给定的 I/O 流。这就是对象在 Julia REPL 中打印的方式。
