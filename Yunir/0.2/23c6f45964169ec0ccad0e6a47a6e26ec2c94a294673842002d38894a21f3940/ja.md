```
encode(s::Union{Char,String}, encoder::AbstractEncoder)
```

カスタム `encoder` を使用して入力 `String` オブジェクトを音訳します。カスタム `encoder` は `@transliterator` を使用して生成されます。
