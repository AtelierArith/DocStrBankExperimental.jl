```
zip_commitfile(w::ZipWriter)
```

オープンしているエントリを閉じて、`w` を書き込み不可にします。エラーが発生した場合、これは [`zip_abortfile`](@ref) のように動作し、その後エラーを再スローします。
