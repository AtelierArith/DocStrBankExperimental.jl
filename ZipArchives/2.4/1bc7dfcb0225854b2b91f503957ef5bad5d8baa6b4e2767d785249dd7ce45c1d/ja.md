### ZipArchives

### Zipアーカイブの読み取り

アーカイブは、zipアーカイブのデータを含む任意の `AbstractVector{UInt8}` から読み取ることができます。

たとえば、githubからこのリポジトリを「.zip」としてダウンロードすると、https://github.com/JuliaIO/ZipArchives.jl/archive/refs/heads/main.zip  READMEをjuliaで読むことができます。

```julia
using ZipArchives: ZipReader, zip_names, zip_readentry
using Downloads: download
data = take!(download("https://github.com/JuliaIO/ZipArchives.jl/archive/refs/heads/main.zip", IOBuffer()));
archive = ZipReader(data)
```

```julia
zip_names(archive)
```

```julia
zip_readentry(archive, "ZipArchives.jl-main/README.md", String) |> print
```

### Zipアーカイブの書き込み

```julia
using ZipArchives: ZipWriter, zip_newfile
using Test: @test_throws
filename = tempname()
```

```julia
ZipWriter(filename) do w
    @test_throws ArgumentError zip_newfile(w, "test\test1.txt")
    zip_newfile(w, "test/test1.txt")
    write(w, "I am data inside test1.txt in the zip file")

    zip_newfile(w, "test/empty.txt")

    zip_newfile(w, "test/test2.txt")
    write(w, "I am data inside test2.txt in the zip file")
end
```
