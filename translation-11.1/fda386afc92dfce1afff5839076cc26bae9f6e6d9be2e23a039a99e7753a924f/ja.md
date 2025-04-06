```
Base64EncodePipe(ostream)
```

書き込み専用の新しいI/Oストリームを返します。これは、書き込まれたバイトを`ostream`に書き込まれるbase64エンコードされたASCIIバイトに変換します。`Base64EncodePipe`ストリームで[`close`](@ref)を呼び出すことは、エンコーディングを完了するために必要です（ただし、`ostream`は閉じません）。

# 例

```jldoctest
julia> io = IOBuffer();

julia> iob64_encode = Base64EncodePipe(io);

julia> write(iob64_encode, "Hello!")
6

julia> close(iob64_encode);

julia> str = String(take!(io))
"SGVsbG8h"

julia> String(base64decode(str))
"Hello!"
```
