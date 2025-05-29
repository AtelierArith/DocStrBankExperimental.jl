StatisticalModelオブジェクトをmPulseリポジトリから削除します

`statModelID`または`statModelName`のいずれかを渡す必要があります。そうしないと、Statistical Modelオブジェクトを削除できません。

### 引数

`token::AbstractString` :    [`getRepositoryToken`](@ref)を呼び出して取得したリポジトリアクセストークン

### キーワード引数

`statModelID::Int64` :    更新する統計モデルのID。

`statModelName::AbstractString` :    mPulseの統計モデル名。これはmPulseドメイン設定ダイアログから取得できます。

### 戻り値

削除が成功した場合はtrueを返し、そうでない場合はfalseを返します。

### 例外

`ArgumentError` :    tokenが空であるか、statModelIDが空である場合

`mPulseAPIException` :    何らかの理由でAPIアクセスに失敗した場合
