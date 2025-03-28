```
ErrorException(msg)
```

一般的なエラータイプです。`.msg`フィールドにあるエラーメッセージは、より具体的な詳細を提供する場合があります。

# 例

```jldoctest
julia> ex = ErrorException("私は悪いことをしました");

julia> ex.msg
"私は悪いことをしました"
```
