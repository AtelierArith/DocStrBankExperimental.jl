REST APIに問題があり、2xx以外のレスポンスを返すときにスローされます。

### フィールド

`msg::AbstractString` :    エラーメッセージ

`response::Response` :    REST API呼び出しからのレスポンスオブジェクト。ヘッダー、データ、クッキー、リダイレクト、および開始リクエストを検査できます。

`responseBody::AbstractString` :    サーバーからのHTTPレスポンスのボディ
