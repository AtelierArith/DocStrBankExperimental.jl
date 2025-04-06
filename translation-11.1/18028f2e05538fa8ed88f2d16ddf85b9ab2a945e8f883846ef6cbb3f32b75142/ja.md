```
approve(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

将来の認証で再利用するために`payload`資格情報を保存します。認証が成功したときのみ呼び出すべきです。

`shred`キーワードは、ペイロード資格情報フィールド内の機密情報を破棄するかどうかを制御します。テスト中は`false`に設定するべきです。
