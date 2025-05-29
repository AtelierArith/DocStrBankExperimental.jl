ZIPアーカイブファイルの読み書きのためのJuliaパッケージ

このパッケージは、JuliaでのZIPアーカイブの読み書きをサポートします。$Pkg.add("ZipFile")$を使用してJuliaパッケージマネージャー経由でインストールしてください。

ZIPファイル形式の詳細は、http://www.pkware.com/documents/casestudies/APPNOTE.TXTに記載されています。

# 例

以下の例では、新しいZIPファイルを書き込み、その後内容を読み戻します。

```
julia> using ZipFile
julia> w = ZipFile.Writer("/tmp/example.zip");
julia> f = ZipFile.addfile(w, "hello.txt");
julia> write(f, "hello world!
");
julia> f = ZipFile.addfile(w, "julia.txt", method=ZipFile.Deflate);
julia> write(f, "Julia
"^5);
julia> close(w)
julia> r = ZipFile.Reader("/tmp/example.zip");
julia> for f in r.files
          println("Filename: $(f.name)")
          write(stdout, read(f, String));
       end
julia> close(r)
Filename: hello.txt
hello world!
Filename: julia.txt
Julia
Julia
Julia
Julia
Julia
```
