テナントオブジェクトをmPulseリポジトリから取得します

`tenantID`または`name`のいずれかを渡す必要があります。これによりテナントを特定します。

テナントはメモリに1時間キャッシュされるため、一致する`tenantID`または`name`を使用した後続の呼び出しは、APIを呼び出すことなく迅速に返されます。これは、リポジトリ内でテナントが変更された場合に問題になる可能性があります。このテナントのキャッシュをクリアするには、[`mPulseAPI.clearTenantCache`](@ref)を使用し、`tenantID`または`name`のいずれかを渡します。

### 引数

`token::AbstractString` :    [`getRepositoryToken`](@ref)を呼び出して取得したリポジトリ認証トークン

### キーワード引数

`tenantID::Int64` :    取得するテナントのID。この方法が最も速いですが、テナントのIDを特定するのは難しい場合があります。

`name::AbstractString` :    mPulse内のテナント名。これはmPulseテナントリストから取得できます。

### 戻り値

`{Dict}` テナントオブジェクトで、以下のフィールドを持ちます：

`name::AbstractString` :    テナントの名前

`id::Int64` :    テナントのID

`body::XMLElement` :    テナントのXML定義を表すXMLオブジェクト、または完全なテナントを見る権限がない場合は空のノード

`parentID::Int64` :    このテナントが属する親フォルダのID

`parentType::AbstractString` :    親オブジェクトのタイプ（通常は`tenantFolder`）

`path::AbstractString` :    このテナントが属するフォルダのパス

`description::AbstractString` :    mPulseに入力されたこのテナントの説明

`created::DateTime` :    このオブジェクトが作成されたタイムスタンプ

`lastModified::DateTime` :    このオブジェクトが作成されたタイムスタンプ

`attributes::Dict` :    このテナントの属性の`Dict`

`dswbUrls::Array{AbstractString}` :    このテナントの有効な認証リダイレクトターゲットであるDSWB URLの配列

### 例外

`ArgumentError` :    トークンが空であるか、`tenantID`と`name`の両方が空の場合

`mPulseAPIException` :    何らかの理由でAPIアクセスに失敗した場合
