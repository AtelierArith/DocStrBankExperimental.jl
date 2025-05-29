ドメインオブジェクトをmPulseリポジトリから取得します

単一のドメインを取得するには、`domainID`、`appKey`、または`appName`のいずれかを渡してドメインを特定する必要があります。これらのいずれも渡されない場合、指定された`token`で読み取れるすべてのドメインが配列として返されます。

ドメインはメモリに1時間キャッシュされるため、一致する`domainID`、`appKey`、または`appName`を使用した後続の呼び出しは、APIを呼び出すことなく迅速に返されます。これは、リポジトリ内でドメインが変更された場合に問題になる可能性があります。このドメインのキャッシュをクリアするには、[`mPulseAPI.clearDomainCache`](@ref)を使用し、`domainID`、`appKey`、または`appName`のいずれかを渡します。

### 引数

`token::AbstractString` :    [`getRepositoryToken`](@ref)を呼び出して取得したリポジトリアクセストークン

### キーワード引数

`domainID::Int64` :    取得するドメインのID。これは最も高速な方法ですが、ドメインのIDを特定するのは難しい場合があります。

`appKey::AbstractString` :    ドメインに関連付けられたアプリキー（以前はAPIキーとして知られていました）。これはmPulseドメイン設定ダイアログから取得できます。

`appName::AbstractString` :    mPulseのアプリ名。これはmPulseドメイン設定ダイアログから取得できます。

### 戻り値

`{Dict|Array{Dict}}` `domainID`、`appKey`、または`appName`のいずれかが渡された場合、単一の`domain`オブジェクトが`Dict`として返されます。

これらのいずれも渡されない場合、すべてのドメインの配列が返され、それぞれが`Dict`です。

`domain` `Dict`には以下のフィールドがあります：

`name` :    アプリの名前

`id::Int64` :    アプリのID

`body::XMLElement` :    アプリのXML定義を表すXMLオブジェクト

`tenantID::Int64` :    このアプリが属するテナントのID

`description::AbstractString` :    mPulseに入力されたこのアプリの説明

`created::DateTime` :    このオブジェクトが作成されたタイムスタンプ

`lastModified::DateTime` :    このオブジェクトが作成されたタイムスタンプ

`attributes::Dict` :    このアプリの属性の`Dict`、`AppKey`を含む

`custom_metrics::Dict` :    データベースのフィールド名にマッピングされたカスタムメトリック名の`{Dict}`で、以下の構造を持ちます：

```julia
Dict(
    <metric name> => Dict(
        "index"        => <index>,                      # 数値インデックス
        "fieldname"    => "custommetric<index>",        # dswbテーブルのフィールド名
        "lastModified" => <lastModifiedDate>,
        "description"  => "<description>",
        "dataType"     => Dict(
            "decimalPlaces"  => "2",
            "type"           => "<metric type>",
            "currencyCode"   => "<ISO 4217 Currency Code if type==Currency>"
        ),
        "colors"       => [<array of color HEX codes>]
    ),
    ...
)
```

`custom_timers::Dict` :    データベースのフィールド名にマッピングされたカスタムタイマー名の`{Dict}`で、以下の構造を持ちます：

```julia
Dict(
    <timer name> => Dict(
        "index"         => <index>,                      # 数値インデックス
        "fieldname"     => "customtimer<index>",         # dswbテーブルのフィールド名
        "mpulseapiname" => "CustomTimer<index>",
        "lastModified"  => <lastModifiedDate>,
        "description"   => "<description>",
        "colors"        => Array(
            Dict(
                "timingType"  => "<seconds | milliseconds>",
                "timingStart" => "<start timer value for this colour range>",
                "timingEnd"   => "<end timer value for this colour range>",
                "colorStart"  => "<start of this color range>",
                "endStart"    => "<end of this color range>"
            ),
            ...
        )
    ),
    ...
)
```

`session_timeout::Int64` :    セッションタイムアウト値（分）

`resource_timing::Bool` :    リソースタイミング収集が有効かどうかを示すフラグ

`vertical_market::AbstractString` :    このドメインが属する垂直市場

### 例外

`ArgumentError` :    トークンが空であるか、`domainID`、`appKey`、`appName`がすべて空の場合

`mPulseAPIException` :    何らかの理由でAPIアクセスに失敗した場合

`Exception` :    リポジトリオブジェクトの解析中に予期しない事態が発生した場合
