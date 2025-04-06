```
setrounding(f::Function, T, mode)
```

`f` fonksiyonu süresince `T` kayan nokta türünün yuvarlama modunu değiştirir. Mantıksal olarak şuna eşdeğerdir:

```
old = rounding(T)
setrounding(T, mode)
f()
setrounding(T, old)
```

Mevcut yuvarlama modları için [`RoundingMode`](@ref) kısmına bakın.
