```
pipeline(from, to, ...)
```

データソースから宛先へのパイプラインを作成します。ソースと宛先はコマンド、I/Oストリーム、文字列、または他の`pipeline`呼び出しの結果であることができます。少なくとも1つの引数はコマンドでなければなりません。文字列はファイル名を指します。2つ以上の引数で呼び出された場合、それらは左から右に連結されます。例えば、`pipeline(a,b,c)`は`pipeline(pipeline(a,b),c)`と同等です。これにより、マルチステージパイプラインをより簡潔に指定する方法が提供されます。

**例**:

```julia
run(pipeline(`ls`, `grep xyz`))
run(pipeline(`ls`, "out.txt"))
run(pipeline("out.txt", `grep xyz`))
```
