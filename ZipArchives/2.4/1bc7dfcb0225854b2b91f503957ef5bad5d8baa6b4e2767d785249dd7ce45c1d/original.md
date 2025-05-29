### ZipArchives

### Reading Zip archives

Archives can be read from any `AbstractVector{UInt8}` containing the data of a zip archive.

For example if you download this repo as a ".zip" from github https://github.com/JuliaIO/ZipArchives.jl/archive/refs/heads/main.zip  you can read the README in julia.

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

### Writing Zip archives

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
