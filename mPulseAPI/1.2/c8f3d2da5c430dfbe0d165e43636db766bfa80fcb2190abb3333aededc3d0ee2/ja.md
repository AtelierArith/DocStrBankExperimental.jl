mPulseリポジトリにログインし、他の呼び出しに使用できる認証トークンを取得します。

トークンはメモリに5時間キャッシュされるため、同じテナントを使用した後続の呼び出しは、APIに呼び出すことなく迅速に返されます。異なる場所からアカウントにサインインしたり、mPulseからログアウトした場合、これが問題になる可能性があります。このトークンのキャッシュは[`mPulseAPI.clearTokenCache`](@ref)を使用してクリアできます。

### 引数

`tenant::AbstractString` :    ログインするテナントの名前。このトークンはこのテナントにバインドされます。

`apiToken::AbstractString` :    APIと認証するためにmPulseによって発行されたapiToken。以前にこのテナントで認証している場合、`apiToken`はキャッシュされており、再度渡す必要はありません。

### 戻り値

`{ASCIIString}` mPulseリポジトリのAuthトークンで、後続のAPI呼び出しの`X-Auth-Token`ヘッダーで使用できます。

### 例外

`ArgumentError` :    テナントまたはapiTokenが空の場合

`mPulseAPIAuthException` :    何らかの理由で認証に失敗した場合
