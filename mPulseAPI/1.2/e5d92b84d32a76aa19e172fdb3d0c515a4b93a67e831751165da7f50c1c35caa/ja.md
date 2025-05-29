REST APIに内部サーバーエラーが発生し、`500 Internal Server Error`を返すときにスローされます。

### フィールド

`msg::AbstractString` :    文字列 "Internal Server Error, please report this. Timestamp: <current unix timestamp in seconds since the epoch>"

`response::Response` :    REST API呼び出しからのレスポンスオブジェクト。ヘッダー、データ、クッキー、リダイレクト、および開始リクエストを検査できます。

`responseBody::AbstractString` :    サーバーからのHTTPレスポンスのボディ
