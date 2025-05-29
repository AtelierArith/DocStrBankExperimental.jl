リクエストパラメータが無効な場合にスローされます

### フィールド

`msg::AbstractString` :    mPulseサーバーから送信されたエラーメッセージ

`code::AbstractString` :    mPulseサーバーから送信されたエラーコード

`parameter::AbstractString` :    mPulseサーバーに問題があったパラメータ

`value::AbstractString` :    mPulseサーバーに問題があったパラメータの値

`response::Response` :    REST API呼び出しからのレスポンスオブジェクト。ヘッダー、データ、クッキー、リダイレクト、および開始リクエストを検査できます。
