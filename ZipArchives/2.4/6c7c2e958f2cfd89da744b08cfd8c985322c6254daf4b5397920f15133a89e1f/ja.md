```
mutable struct ZipWriter{S<:IO} <: IO
ZipWriter(io::IO; zip_kwargs...)::ZipWriter{typeof(io)}
ZipWriter(f::Function, io::IO; zip_kwargs...)::ZipWriter{typeof(io)}
```

`io`にzipアーカイブライターを作成します。

これらのメソッドは、`io::IO`の代わりに`filename::AbstractString`でも動作します。

その場合、渡されたすべてのキーワード引数は、`write=true`に加えて`Base.open`に使用されます。

`ZipWriter`が閉じられる前に`io`は変更されてはなりません（ラッピングされた`ZipWriter`を使用する場合を除く）。

`ZipWriter`は、[`zip_newfile`](@ref)への呼び出しの後に書き込み可能な`IO`になります。

```
zip_newfile(w::ZipWriter, name::AbstractString; newfile_kwargs...)
```

`ZipWriter`への書き込みは、最後に指定された新しいファイルに書き込まれます。

`ZipWriter`が書き込み可能な状態で[`zip_newfile`](@ref)が呼び出されると、前のファイルはアーカイブにコミットされます。以前に書き込まれたデータを編集する方法はありません。

[`zip_newfile`](@ref)の代替として[`zip_writefile`](@ref)があります。

```
zip_writefile(w::ZipWriter, name::AbstractString, data::AbstractVector{UInt8})
```

これは、`w`のファイルエントリにデータのベクトルを直接書き込みます。[`zip_newfile`](@ref)とは異なり、[`zip_writefile`](@ref)を使用する場合は、`io`がシーク可能である必要はありません。

`ZipWriter`の`Base.close`は、`zip_kwargs`に`own_io=true`が含まれているか、`ZipWriter`がファイル名から作成された場合にのみ、ラップされた`io`を閉じます。

# マルチスレッド

単一の`ZipWriter`インスタンスは、複数のスレッドからの変更や書き込みを同時に許可しません。

# 追加

`ZipWriter`は`io`が空であることを前提としています。既存のデータがある`io`に書き込もうとすると、無効なアーカイブになります。

既存のzipアーカイブにエントリを追加したい場合は、[`zip_append_archive`](@ref)を使用してください。

# オプションのキーワード

  * `check_names::Bool=true`: 新しいエントリ名がWindowsで無効であるか、アーカイブ内に大文字と小文字を区別せずに既に存在する場合にエラーを最善を尽くして試みます。
