```
addenv(command::Cmd, env...; inherit::Bool = true)
```

新しい環境マッピングを指定された [`Cmd`](@ref) オブジェクトにマージし、新しい `Cmd` オブジェクトを返します。重複するキーは置き換えられます。`command` に既に環境値が設定されていない場合、`inherit` が `true` の場合は `addenv()` 呼び出し時の現在の環境を継承します。値が `nothing` のキーは環境から削除されます。

関連情報としては、[`Cmd`](@ref)、[`setenv`](@ref)、[`ENV`](@ref) があります。

!!! compat "Julia 1.6"
    この関数は Julia 1.6 以降が必要です。

