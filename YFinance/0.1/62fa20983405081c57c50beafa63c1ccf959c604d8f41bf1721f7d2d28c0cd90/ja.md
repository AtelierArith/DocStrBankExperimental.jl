```
create_proxy_settings(p::AbstractString,user=nothing,password=nothing)
```

グローバルプロキシ変数 `_PROXY_SETTINGS::NamedTuple` を設定します。この `NamedTuple` には `proxy` と `auth` フィールドが含まれています。これらのフィールドはそれぞれ `nothing` と空の `Dict` にデフォルト設定されています。

## 引数

  * p`::String` (必須) の形式: "http://proxy.xyz.com:8080"
  * user`::String` ユーザー名 (オプション) プロキシが認証を必要とする場合のみ必須。デフォルトは `nothing` (認証不要)
  * password`::String` ユーザー名に対応するパスワード。デフォルトは `nothing` (認証不要)
