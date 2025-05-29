非シークストリームからZIPアーカイブファイルを読み取るためのJuliaパッケージ。

このパッケージは、JuliaでZIPアーカイブの読み書きをサポートします。`Pkg.add("ZipStreams")`を使用してJuliaパッケージマネージャー経由でインストールしてください。

ZIPファイル形式の詳細はhttp://www.pkware.com/documents/casestudies/APPNOTE.TXTに記載されています。

# 例

以下の例では、ZIPアーカイブを作成し、ファイルを書き込み、その後同じアーカイブを開いてファイルの内容をコンソールに出力します。

```julia
using ZipStreams

zipsink("archive.zip") do sink     # "do"構文を使用したシンクのコンテキスト管理
    open(sink, "hello.txt") do f   # "do"構文を使用したファイルのコンテキスト管理
        write(f, "Hello, Julia!")  # 任意のIOオブジェクトに書き込むように書き込みます
    end
end

zipsource("archive.zip") do source   # "do"構文を使用したソースのコンテキスト管理
    for f in source                  # アーカイブ内のファイルを反復処理
        println(info(f).name)        # "hello.txt"
        read_data = read(String, f)  # 任意のIOオブジェクトから読み取るように読み取ります
        println(read_data)           # "Hello, Julia!"
    end
end
```
