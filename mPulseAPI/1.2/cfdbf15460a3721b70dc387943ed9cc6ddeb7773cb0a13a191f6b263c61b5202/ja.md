mPulseリポジトリからStatisticalModelオブジェクトを取得します

`statModelID`または`statModelName`のいずれかを渡す必要があり、統計モデルを特定します。

統計モデルはメモリに1時間キャッシュされるため、一致する`statModelID`を使用した後続の呼び出しは、APIを呼び出すことなく迅速に返されます。これは、リポジトリ内の統計モデルが変更された場合に問題になる可能性があります。このテナントのキャッシュをクリアするには、[`mPulseAPI.clearStatModelCache`](@ref)を使用し、`statModelID`を渡します。

### 引数

`token::AbstractString` :    [`getRepositoryToken`](@ref)を呼び出して取得したリポジトリ認証トークン

### キーワード引数

`statModelID::Int64` :    更新する統計モデルのID。

`statModelName::AbstractString` :    mPulse内の統計モデル名。これはmPulseドメイン設定ダイアログから取得できます。

### 戻り値

`{Dict}` `statisticalmodel`オブジェクトで、以下のフィールドを持ちます：

`hidden::Bool` :    統計モデルがユーザーに表示されるかどうかを示すフラグ

`parentID::Int64` :    この統計モデルが含まれている親フォルダのID

`path::AbstractString` :    この統計モデルが含まれているフォルダのパス

`readOnly::Bool` :    統計モデルが編集可能かどうかを示すフラグ

`name::AbstractString` :    統計モデルの名前

`tenantID::Int64` :    この統計モデルが含まれているテナントのID

`created::DateTime` :    このオブジェクトが作成されたタイムスタンプ

`id::Int64` :    統計モデルのID。

`description::AbstractString` :    mPulseに入力されたこの統計モデルの説明

`lastCached::DateTime` :    このオブジェクトが最後にキャッシュされたタイムスタンプ

`body::XMLElement` :    統計モデルのXML定義を表すXMLオブジェクト、または完全な統計モデルを見る権限がない場合は空のノード

`references::Dict` :    `name`、`id`、`type`、`path`などの参照情報を持つ`Dict`の配列。

`uid::AbstractString` :    統計モデルに関連付けられた暗号化されたuid

`deleted::Bool` :    統計モデルが削除されたかどうかを示すフラグ

`ownerID::Int64` :    統計モデルの所有者のID

`attributes::Dict` :    統計モデルがアクティブであるか、バージョン番号、統計モデルが最後にクリアされた、トリガーされた、更新された時間を含む`Dict`。

`lastModified::DateTime` :    このオブジェクトが作成されたタイムスタンプ

### 例外

`ArgumentError` :    tokenが空またはstatModelIDが空の場合

`mPulseAPIException` :    何らかの理由でAPIアクセスに失敗した場合
