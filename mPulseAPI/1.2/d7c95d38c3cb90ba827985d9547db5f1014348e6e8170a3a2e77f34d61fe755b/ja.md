アラートオブジェクトをmPulseリポジトリから削除します

アラートオブジェクトを削除するには、`alertID`または`alertName`のいずれかを渡す必要があります。

### 引数

`token::AbstractString` :    [`getRepositoryToken`](@ref)を呼び出して取得したリポジトリアクセストークン

### キーワード引数

`alertID::Int64` :    更新するアラートのID。

`alertName::AbstractString` :    mPulseのアラート名。これはmPulseドメイン設定ダイアログから取得できます。

### 戻り値

削除が成功した場合はtrueを返し、そうでない場合はfalseを返します。

### 例外

`ArgumentError` :    tokenが空またはalertIDが空の場合

`mPulseAPIException` :    何らかの理由でAPIアクセスに失敗した場合
