```
chown(path::AbstractString, owner::Integer, group::Integer=-1)
```

`path`'in sahibi ve/veya grubunu `owner` ve/veya `group` olarak değiştirir. `owner` veya `group` için girilen değer `-1` ise, ilgili ID değişmeyecektir. Şu anda yalnızca tam sayı `owner` ve `group` desteklenmektedir. `path`'i döndür.
