```
islocked(lock) -> ステータス (ブール値)
```

`lock`が任意のタスク/スレッドによって保持されているかどうかを確認します。この関数単独では同期に使用すべきではありません。しかし、`islocked`を[`trylock`](@ref)と組み合わせることで、*`typeof(lock)`*がサポートしている場合に限り、テスト・アンド・テスト・アンド・セットや指数バックオフアルゴリズムを書くために使用できます（そのドキュメントを参照してください）。

# 拡張ヘルプ

例えば、以下のように`lock`の実装が下記のプロパティを満たす場合、指数バックオフを実装できます。

```julia
nspins = 0
while true
    while islocked(lock)
        GC.safepoint()
        nspins += 1
        nspins > LIMIT && error("タイムアウト")
    end
    trylock(lock) && break
    backoff()
end
```

## 実装

ロックの実装は、以下のプロパティを持つ`islocked`を定義し、そのことをドキュメントに記載することを推奨します。

  * `islocked(lock)`はデータ競合がありません。
  * `islocked(lock)`が`false`を返す場合、他のタスクからの干渉がなければ、`trylock(lock)`の即時呼び出しは成功しなければなりません（`true`を返す）。
