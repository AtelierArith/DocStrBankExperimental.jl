```
send!(lk::Link, m::Message)
send!(name::Symbol, m::Message)
```

メッセージ `m` をアクター `lk` または `name` （登録されている場合）に送信します。
