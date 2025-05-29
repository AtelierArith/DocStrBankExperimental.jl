```
zip_append_archive(io::IO; trunc_footer=true, zip_kwargs=(;))::ZipWriter
```

既存のzipアーカイブにエントリを追加する`ZipWriter`を返します。

これは、`io::IO`の代わりに`filename::AbstractString`でも動作します。その場合、渡されたすべてのキーワード引数は、`read=true, write=true`に加えて`Base.open`に使用されます。

`io`に有効なzipアーカイブのフッターがすでにない場合、この関数はエラーになります。

`trunc_footer=true`の場合、`io`の最後にある不要なzipアーカイブのフッターは切り捨てられます。そうでない場合は、そのままにされます。

`zip_kwargs`は[`ZipWriter`](@ref)に転送されます。
