```
SpinLock()
```

再入不可のテスト・アンド・テスト・アンド・セットスピンロックを作成します。再帰的な使用はデッドロックを引き起こします。この種のロックは、実行にかかる時間が短く、ブロックしないコードの周りでのみ使用するべきです（例：I/Oを実行する）。一般的には、[`ReentrantLock`](@ref)を代わりに使用するべきです。

各[`lock`](@ref)は[`unlock`](@ref)と対になっている必要があります。もし[`!islocked(lck::SpinLock)`](@ref islocked)が成り立つ場合、[`trylock(lck)`](@ref trylock)は、他のタスクが「同時に」ロックを保持しようとしていない限り成功します。

テスト・アンド・テスト・アンド・セットスピンロックは、約30の競合スレッドまでが最も速いです。それ以上の競合がある場合は、異なる同期アプローチを検討する必要があります。
