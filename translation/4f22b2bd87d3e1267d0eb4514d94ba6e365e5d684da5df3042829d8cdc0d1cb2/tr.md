```
pttrs!(D, E, B)
```

`A * X = B` için pozitif tanımlı üçlü diagonal `A`'yı, `D` ile diagonal ve `E` ile off-diagonal olarak çözmektedir. `A`'nın LDLt faktorizasyonu `pttrf!` kullanılarak hesaplandıktan sonra `B`, çözüm `X` ile üzerine yazılır.
