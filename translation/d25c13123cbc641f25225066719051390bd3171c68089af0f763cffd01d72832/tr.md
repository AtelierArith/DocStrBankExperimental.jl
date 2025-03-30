```
@goto name
```

`@goto name` koşulsuz olarak [`@label name`](@ref) konumundaki ifadeye atlar.

`@label` ve `@goto` farklı üst düzey ifadelere atlamalar oluşturamaz. Denemeler bir hata ile sonuçlanır. Yine de `@goto` kullanmak için, `@label` ve `@goto`'yu bir blok içinde kapsayın.
