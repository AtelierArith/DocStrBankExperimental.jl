```
gglse!(A, c, B, d) -> (X,res)
```

`A * x = c` denklemini çözer; burada `x`, `B * x = d` eşitlik kısıtlamasına tabidir. Çözüm için `||c - A*x||^2 = 0` formülünü kullanır. `X` ve kalıntı kareler toplamını döner.
