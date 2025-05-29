```
setiparams([f], block, itr)
setiparams([f], block, params...)
```

`block`のパラメータを設定します。非インプレースバージョンです。`f`が提供されると、`block`のパラメータを`collection`内の`f`によってマッピングされた値に設定します。`iter`はイテレータまたはシンボルであり、シンボルは`:zero`または`:random`であることができます。
