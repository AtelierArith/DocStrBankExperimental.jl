アラートオブジェクトをmPulseリポジトリから取得します

`alertID`または`alertName`のいずれかを渡す必要があります。どちらも渡されない場合、テナントのすべてのアラートが返されます。

アラートは1時間メモリにキャッシュされるため、一致する`alertID`を使用した後続の呼び出しは、APIを呼び出すことなく迅速に返されます。これは、リポジトリ内のアラートが変更された場合に問題になる可能性があります。このテナントのキャッシュをクリアするには、[`mPulseAPI.clearAlertCache`](@ref)を使用し、`alertID`を渡します。

### 引数

`token::AbstractString` :    [`getRepositoryToken`](@ref)を呼び出して取得したリポジトリ認証トークン

### キーワード引数

`alertID::Int64` :    取得するアラートのID。

`alertName::AbstractString` :    mPulseのアラート名。これはmPulseドメイン設定ダイアログから取得できます。

### 戻り値

`{Dict}` アラートオブジェクトで、以下のフィールドを持ちます：

`hidden::Bool` :    アラートがユーザーに表示されるかどうかを示すフラグ

`parentID::Int64` :    このアラートが含まれる親フォルダのID

`path::AbstractString` :    このアラートが含まれるフォルダのパス

`readOnly::Bool` :    アラートが編集可能かどうかを示すフラグ

`name::AbstractString` :    アラートの名前

`tenantID::Int64` :    アラートが含まれるテナントのID

`created::DateTime` :    このオブジェクトが作成されたタイムスタンプ

`id::Int64` :    アラートのID。

`description::AbstractString` :    mPulseに入力されたこのアラートの説明

`lastCached::DateTime` :    このオブジェクトが最後にキャッシュされたタイムスタンプ

`body::XMLElement` :    アラートのXML定義を表すXMLオブジェクト、または完全なアラートを見る権限がない場合は空のノード

`references::Dict` :    `name`、`id`、`type`、`path`などの参照情報を持つ`Dict`の配列。

`uid::AbstractString` :    アラートに関連付けられた暗号化されたuid

`deleted::Bool` :    アラートが削除されたかどうかを示すフラグ

`ownerID::Int64` :    アラートの所有者のID

`attributes::Dict` :    アラートがアクティブかどうか、バージョン番号、アラートが最後にクリアされた、トリガーされた、更新された時間を含む`Dict`。

`lastModified::DateTime` :    このオブジェクトが作成されたタイムスタンプ

### 例外

`ArgumentError` :    トークンが空またはalertIDが空の場合

`mPulseAPIException` :    何らかの理由でAPIアクセスに失敗した場合
