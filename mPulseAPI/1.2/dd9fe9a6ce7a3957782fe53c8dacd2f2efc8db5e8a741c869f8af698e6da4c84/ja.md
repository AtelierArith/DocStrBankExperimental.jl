mPulseリポジトリからStatisticalModelオブジェクトを更新します

`statModelID`または`statModelName`のいずれかを渡す必要があります。統計モデルオブジェクトを更新するためです。

### 引数

`token::AbstractString` :    [`getRepositoryToken`](@ref)を呼び出して取得したリポジトリアクセストークン

### キーワード引数

`statModelID::Int64` :    更新する統計モデルのID。

`statModelName::AbstractString` :    mPulseの統計モデル名。これはmPulseドメイン設定ダイアログから取得できます。

`attributes::Dict` :    更新する統計モデル属性の`Dict`

`objectFields::Dict` :    更新する統計モデルオブジェクトフィールドの`Dict`

`body::AbstractString|LightXML.XMLElement=""` :    統計モデルの本文を含むXMLElement（空でない場合）、エラーに関する関連情報を含みます。

### 戻り値

`{Dict}` 更新された`statistical model`オブジェクトで、以下のフィールドを含みます：

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

`errorXML::Union{AbstractString, LightXML.XMLElement}` :    リポジトリによって更新されるアラートのXMLエラー定義を表すXMLオブジェクト。

`references::Dict` :    `name`、`id`、`type`、および`path`などの参照情報を含む`Dict`の配列。

`uid::AbstractString` :    統計モデルに関連付けられた暗号化されたuid

`deleted::Bool` :    統計モデルが削除されたかどうかを示すフラグ

`ownerID::Int64` :    統計モデルの所有者のID

`attributes::Dict` :    統計モデルがアクティブであるか、バージョン番号、統計モデルが最後にクリアされた、トリガーされた、更新された時間を含む`Dict`。

`lastModified::DateTime` :    このオブジェクトが作成されたタイムスタンプ

### 例外

`ArgumentError` :    トークンが空またはstatModelIDが空の場合

`mPulseAPIException` :    何らかの理由でAPIアクセスに失敗した場合
