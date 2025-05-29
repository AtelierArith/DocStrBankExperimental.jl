無効または期限切れのトークンを使用してREST APIに認証する際にスローされます

### フィールド

`msg::AbstractString` :    このメッセージは常に「REST APIでの認証エラー」に設定されます

`response::Response` :    REST API呼び出しからの応答オブジェクト。ヘッダー、データ、クッキー、リダイレクト、および開始リクエストを検査できます。

`responseBody::AbstractString` :    サーバーからのHTTP応答のボディ
