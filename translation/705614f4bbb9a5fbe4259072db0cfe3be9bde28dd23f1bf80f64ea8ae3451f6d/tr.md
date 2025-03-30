```
readdlm(source, delim::AbstractChar, T::Type, eol::AbstractChar; header=false, skipstart=0, skipblanks=true, use_mmap, quotes=true, dims, comments=false, comment_char='#')
```

Kaynağından bir matris okuyun; her satır (`eol` ile ayrılmış) bir satır verir ve elemanlar verilen ayırıcı ile ayrılır. Kaynak bir metin dosyası, akış veya bayt dizisi olabilir. Bellek haritalı dosyalar, haritalanmış segmentin bayt dizisi temsili kaynak olarak geçildiğinde kullanılabilir.

Eğer `T` bir sayısal türse, sonuç o türde bir dizi olur; sayısal olmayan elemanlar, kayan nokta türleri için `NaN` veya sıfır olarak değerlendirilir. `T` için diğer yararlı değerler `String`, `AbstractString` ve `Any`'dir.

Eğer `header` `true` ise, verilerin ilk satırı başlık olarak okunur ve yalnızca `data_cells` yerine `(data_cells, header_cells)` tuple'ı döndürülür.

`skipstart` belirtmek, girişten karşılık gelen sayıda başlangıç satırını yok sayar.

Eğer `skipblanks` `true` ise, girişteki boş satırlar yok sayılacaktır.

Eğer `use_mmap` `true` ise, `source` tarafından belirtilen dosya, büyükse potansiyel hız artışları için bellek haritalıdır. Varsayılan `false`'dur. Bir Windows dosya sisteminde, `use_mmap` yalnızca dosya bir kez okunuyorsa ve yazılmıyorsa `true` olarak ayarlanmamalıdır. Bir işletim sistemi Unix benzeri olup dosya sistemi Windows benzeri olan bazı kenar durumları vardır.

Eğer `quotes` `true` ise, çift tırnak (") karakterleri içinde yer alan sütunların yeni satırlar ve sütun ayırıcıları içermesine izin verilir. Alıntılanmış bir alandaki çift tırnak karakterleri, başka bir çift tırnak ile kaçırılmalıdır. Beklenen satır ve sütunların (varsa başlık dahil) bir tuple'ı olarak `dims` belirtmek, büyük dosyaların okunmasını hızlandırabilir. Eğer `comments` `true` ise, `comment_char` ile başlayan satırlar ve herhangi bir satırdaki `comment_char`'dan sonraki metin yok sayılır.

# Örnekler

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [5; 6; 7; 8];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end

julia> readdlm("delim_file.txt", '\t', Int, '\n')
4×2 Matrix{Int64}:
 1  5
 2  6
 3  7
 4  8

julia> rm("delim_file.txt")
```
