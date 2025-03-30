```
potrs!(uplo, A, B)
```

`A * X = B` denkleminin çözümünü bulur; burada `A`, `potrf!` ile hesaplanmış Cholesky ayrışımına sahip simetrik veya Hermit pozitif tanımlı bir matristir. Eğer `uplo = U` ise, `A`'nın üst Cholesky ayrışımı hesaplanmıştır. Eğer `uplo = L` ise, `A`'nın alt Cholesky ayrışımı hesaplanmıştır. `B`, çözüm `X` ile üzerine yazılır.
