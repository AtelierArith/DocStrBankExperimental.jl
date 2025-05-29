```
mutable struct Message <: AbstractArray{UInt8, 1}
```

共有バッファでZMQメッセージを送受信するための高レベルの`Message`オブジェクトです。`AbstractArray`として、一般的な（サイズ変更不可の）配列の動作をサポートします。

# 例

```jldoctest
julia> using ZMQ

julia> m = Message("foo");

julia> Char(m[1])            # 配列インデックス
'f': ASCII/Unicode U+0066 (category Ll: Letter, lowercase)

julia> m[end] = Int('g');    # 配列代入

julia> unsafe_string(m)      # 文字列への変換（メッセージが文字列であることが分かっている場合のみ行ってください）
"fog"

julia> IOBuffer(m)           # ゼロコピーのIOBufferを作成
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=3, maxsize=Inf, ptr=1, mark=-1)
```
