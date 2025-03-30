```
devnull
```

Yazılan tüm verileri atmak için bir akış yönlendirmesinde kullanılır. Temelde Unix'teki `/dev/null` veya Windows'taki `NUL` ile eşdeğerdir. Kullanım:

```julia
run(pipeline(`cat test.txt`, devnull))
```
