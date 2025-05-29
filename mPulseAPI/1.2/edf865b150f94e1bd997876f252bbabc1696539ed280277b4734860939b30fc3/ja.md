mPulseリポジトリからAlertオブジェクトを更新します

アラートオブジェクトを更新するには、`alertID`または`alertName`のいずれかを渡す必要があります。

### 引数

`token::AbstractString` :    [`getRepositoryToken`](@ref)を呼び出して取得したリポジトリアクセストークン

### キーワード引数

`alertID::Int64` :    更新するアラートのID。

`alertName::AbstractString` :    mPulseのアラート名。これはmPulseドメイン設定ダイアログから取得できます。

`attributes::Dict` :    更新するアラート属性の`Dict`

`objectFields::Dict` :    更新するアラートオブジェクトフィールドの`Dict`

`body::AbstractString|LightXML.XMLElement=""` :    アラートの本文を含むXMLElement（空でない場合）、エラーに関する関連情報を含みます。

### 戻り値

`{Dict}` 更新された`alert`オブジェクトで、以下のフィールドを含みます：

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

`errorXML::Union{AbstractString, LightXML.XMLElement}` :    リポジトリによって更新されるアラートのXMLエラー定義を表すXMLオブジェクト。

`references::Dict` :    `name`、`id`、`type`、および`path`などの参照情報を含む`Dict`の配列。

`uid::AbstractString` :    アラートに関連付けられた暗号化されたuid

`deleted::Bool` :    アラートが削除されたかどうかを示すフラグ

`ownerID::Int64` :    アラートの所有者のID

`attributes::Dict` :    アラートがアクティブであるか、バージョン番号、アラートが最後にクリアされた、トリガーされた、更新された時間を含む`Dict`。

`lastModified::DateTime` :    このオブジェクトが作成されたタイムスタンプ

### 例外

`ArgumentError` :    トークンが空であるか、alertIDが空の場合

`mPulseAPIException` :    何らかの理由でAPIアクセスに失敗した場合
