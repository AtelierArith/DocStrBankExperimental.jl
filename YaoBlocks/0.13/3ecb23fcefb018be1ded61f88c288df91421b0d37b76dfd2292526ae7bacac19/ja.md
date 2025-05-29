```
setiparams!([f], block, itr)
setiparams!([f], block, params...)
```

`block`のパラメータを設定します。`f`が提供されている場合、`block`のパラメータを`collection`内の`f`によってマッピングされた値に設定します。`iter`はイテレータまたはシンボルであり、シンボルは`:zero`または`:random`であることができます。
