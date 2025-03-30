```
rm(path::AbstractString; force::Bool=false, recursive::Bool=false)
```

Verilen yoldaki dosyayı, bağlantıyı veya boş dizini siler. Eğer `force=true` geçilirse, var olmayan bir yol hata olarak değerlendirilmez. Eğer `recursive=true` geçilirse ve yol bir dizin ise, tüm içerikler özyinelemeli olarak silinir.

# Örnekler

```jldoctest
julia> mkpath("my/test/dir");

julia> rm("my", recursive=true)

julia> rm("this_file_does_not_exist", force=true)

julia> rm("this_file_does_not_exist")
HATA: IOError: unlink("this_file_does_not_exist"): böyle bir dosya veya dizin yok (ENOENT)
Yığın izi:
[...]
```
