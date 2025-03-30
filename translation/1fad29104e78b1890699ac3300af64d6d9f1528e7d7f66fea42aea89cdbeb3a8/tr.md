```
LibGit2.git_url(; kwargs...) -> String
```

Verilen URL bileşenlerine dayalı bir dize oluşturur. `scheme` anahtar kelimesi sağlanmadığında üretilen URL, alternatif [scp-benzeri sözdizimini](https://git-scm.com/docs/git-clone#_git_urls_a_id_urls_a) kullanacaktır.

# Anahtar Kelimeler

  * `scheme::AbstractString=""`: kullanılacak protokolü tanımlayan URL şeması. HTTP için "http", SSH için "ssh" vb. `scheme` sağlanmadığında çıktı formatı "ssh" olacak ancak scp-benzeri sözdizimini kullanacaktır.
  * `username::AbstractString=""`: sağlandığında çıktıda kullanılacak kullanıcı adı.
  * `password::AbstractString=""`: sağlandığında çıktıda kullanılacak şifre.
  * `host::AbstractString=""`: çıktıda kullanılacak ana bilgisayar adı. Bir ana bilgisayar adının belirtilmesi gerekmektedir.
  * `port::Union{AbstractString,Integer}=""`: sağlandığında çıktıda kullanılacak port numarası. scp-benzeri sözdizimi kullanıldığında belirtilemez.
  * `path::AbstractString=""`: sağlandığında çıktıda kullanılacak yol.

!!! uyarı     URL'lerde şifre kullanmaktan kaçının. Kimlik bilgisi nesnelerinin aksine, Julia hassas verileri kullanımdan sonra güvenli bir şekilde sıfırlayamaz veya yok edemez ve şifre bellek içinde kalabilir; bu da belirsiz bir bellek tarafından ifşa edilebilir.

# Örnekler

```jldoctest
julia> LibGit2.git_url(username="git", host="github.com", path="JuliaLang/julia.git")
"git@github.com:JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="https", host="github.com", path="/JuliaLang/julia.git")
"https://github.com/JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="ssh", username="git", host="github.com", port=2222, path="JuliaLang/julia.git")
"ssh://git@github.com:2222/JuliaLang/julia.git"
```
