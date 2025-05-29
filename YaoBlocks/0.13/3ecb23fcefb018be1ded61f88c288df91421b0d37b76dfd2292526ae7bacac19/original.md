```
setiparams!([f], block, itr)
setiparams!([f], block, params...)
```

Set the parameters of `block`. When `f` is provided, set parameters of `block` to the value in `collection` mapped by `f`. `iter` can be an iterator or a symbol, the symbol can be `:zero`, `:random`.
