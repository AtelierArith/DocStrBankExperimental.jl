内部の便利関数。リポジトリからオブジェクトを取得し、適切なキャッシュオブジェクトに1時間キャッシュします。

  * `searchKey`が渡され、`filterRequired`が`true`（デフォルト）に設定されている場合、単一のオブジェクトを返します。
  * `searchKey`が渡されず、`filterRequired`が`false`に設定されている場合、オブジェクトの配列を返します。
  * `searchKey`が渡されず、`filterRequired`が`true`に設定されている場合、例外をスローします。
