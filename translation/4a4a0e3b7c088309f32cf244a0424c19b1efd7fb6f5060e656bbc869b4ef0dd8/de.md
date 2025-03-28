```
RawFD
```

Primitiver Typ, der den nativen OS-Dateideskriptor umschließt. `RawFD`s können an Methoden wie [`stat`](@ref) übergeben werden, um Informationen über die zugrunde liegende Datei zu erhalten, und können auch verwendet werden, um Streams zu öffnen, wobei der `RawFD` die OS-Datei beschreibt, die den Stream unterstützt.
