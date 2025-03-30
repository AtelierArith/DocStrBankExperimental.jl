# [StyledStrings](@id stdlib-styledstrings)

```@meta
CurrentModule = StyledStrings
DocTestSetup = quote
    using StyledStrings
end
```

!!! note
    StyledStrings ve AnnotatedStrings için API deneysel olarak kabul edilmektedir ve Julia sürümleri arasında değişiklik göstermesi muhtemeldir.


## [Styling](@id stdlib-styledstrings-styling)

Dizelerle çalışırken, biçimlendirme ve stil genellikle ikincil bir endişe olarak ortaya çıkar.

Örneğin, bir terminale yazdırırken [ANSI escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code#SGR_(Select_Graphic_Rendition)_parameters) çıktısında serpiştirmek isteyebilirsiniz, HTML stil yapıları (`<span style="...">` vb.) benzer bir amaca hizmet eder ve devam eder. İçerikle birlikte ham stil yapıları dizeye basitçe eklemek mümkündür, ancak bu, en temel kullanım durumları dışında iyi bir şekilde uygun olmadığını hızla ortaya çıkarır. Tüm terminaller aynı ANSI kodlarını desteklemez, stil yapıları, zaten stillendirilmiş içeriğin genişliğini hesaplarken titizlikle kaldırılmalıdır ve bu, birden fazla çıktı formatını ele almaya başlamadan önceki durumdur.

Bunu aşağı akışta yaygın olarak deneyimlenmesi için bırakmak yerine, özel bir dize türünün ([`AnnotatedString`](@ref Base.AnnotatedString)) tanıtımıyla doğrudan ele alınmaktadır. Bu dize türü, herhangi bir [`AbstractString`](@ref) türünü sarar ve biçimlendirme bilgilerini bölgelere uygulamaya olanak tanır (örneğin, 1'den 7'ye kadar olan karakterler kalın ve kırmızıdır).

Bir dize bölgeleri, onlara [`Face`](@ref StyledStrings.Face) (düşünün "yazı tipi") uygulayarak stillendirilir — stil bilgilerini tutan bir yapı. Kolaylık olması açısından, küresel yüzler sözlüğündeki yüzler (örneğin `shadow`) doğrudan `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` vermek yerine sadece adlandırılabilir.

Bu yeteneklerin yanı sıra, [`AnnotatedString`](@ref Base.AnnotatedString) oluşturmak için de kullanışlı bir yol sağlıyoruz, bu da [Styled String Literals](@ref stdlib-styledstring-literals) içinde detaylandırılmıştır.

```@repl demo
using StyledStrings
styled"{yellow:hello} {blue:there}"
```

## [Annotated Strings](@id man-annotated-strings)

Bazen bir dize ile ilgili bölgeleri tutmak için meta verileri saklamak faydalı olabilir. Bir [`AnnotatedString`](@ref Base.AnnotatedString), başka bir dizeyi sarar ve bunun bölgelerinin etiketli değerlerle (`:label => value`) anotasyon yapılmasına olanak tanır. Tüm genel dize işlemleri, temel dizeye uygulanır. Ancak, mümkün olduğunda stil bilgileri korunur. Bu, bir `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` üzerinde alt dizeler alabileceğiniz, bunları doldurabileceğiniz, diğer dizelerle birleştirebileceğiniz anlamına gelir ve meta veri anotasyonları "yolda gelir".

Bu dize türü, stil bilgilerini tutmak için `:face` etiketli notlar kullanan [StyledStrings stdlib](@ref stdlib-styledstrings) için temeldir.

[`AnnotatedString`](@ref Base.AnnotatedString) ile birleştirirken, dize açıklamalarını korumak istiyorsanız [`annotatedstring`](@ref StyledStrings.annotatedstring) kullanmaya dikkat edin, [`string`](@ref) yerine.

```jldoctest
julia> str = AnnotatedString("hello there", [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
AnnotatedString{String}

julia> str2 = AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == annotatedstring(str, str2) # *-concatenation works
true
```

[`AnnotatedString`](@ref Base.AnnotatedString) anotasyonları [`annotations`](@ref StyledStrings.annotations) ve [`annotate!`](@ref StyledStrings.annotate!) fonksiyonları aracılığıyla erişilebilir ve değiştirilebilir.

## Styling via [`AnnotatedString`](@ref Base.AnnotatedString)s

## [Faces](@id stdlib-styledstrings-faces)

### The `Face` type

Bir [`Face`](@ref StyledStrings.Face), metinlerin ayarlanabileceği bir yazı tipinin ayrıntılarını belirtir. Farklı formatlar arasında iyi bir şekilde genelleştirilebilen temel özellikler kümesini kapsar, yani:

  * `yazı tipi`
  * `yükseklik`
  * `ağırlık`
  * `eğim`
  * `ön plan`
  * `arka plan`
  * `altı çizili`
  * `üstü çizili`
  * `ters`
  * `miras almak`

Belirli niteliklerin bu biçimlerinin ayrıntıları için [`Face`](@ref StyledStrings.Face) docstring'ine bakın, ancak özellikle ilginç olan `inherit`'dir çünkü diğer `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`'lerden nitelikleri *devralmanıza* olanak tanır.

### The global faces dictionary

Belirli stillere atıfta bulunmayı daha uygun hale getirmek için, `Dict{Symbol, Face}` adlı küresel bir yapı vardır. Bu yapı, [`Face`](@ref StyledStrings.Face)'leri sadece isimle anılmasını sağlar. Paketler, bu sözlüğe yüzler eklemek için [`addface!`](@ref StyledStrings.addface!) fonksiyonunu kullanabilir ve yüklenen yüzler kolayca [customized](@ref stdlib-styledstrings-face-toml) olarak kullanılabilir.

!!! warning "Appropriate face naming"
    Herhangi bir paket yeni yüzler kaydediyorsa, bunların paket adıyla ön eklenmiş olduğundan emin olmalıdır, yani `mypackage_myface` formatını takip etmelidir. Bu, öngörülebilirlik açısından önemlidir ve isim çakışmalarını önlemek için gereklidir.

    Ayrıca, paketlerin doğrudan renkler ve stiller (örneğin `cyan`) yerine *anlamsal* yüzleri (örneğin `code`) kullanmaya (ve tanıtmaya) özen göstermesi gerekir. Bu, kullanım amacını daha belirgin hale getirmek, bileşenlerin birleştirilmesine yardımcı olmak ve kullanıcı özelleştirmesini daha sezgisel hale getirmek gibi birçok açıdan faydalıdır.


Paket ön ek kuralına iki tür muafiyet vardır:

  * varsayılan değer olan yüzler sözlüğünün bir parçası olan temel yüzlerin kümesi
  * Julia'nın kendi standart kütüphanesi tarafından tanıtılan yüzler, yani `JuliaSyntaxHighlighting`

#### [Basic faces](@id stdlib-styledstrings-basic-faces)

Temel yüzler, yaygın olarak uygulanabilir genel bir fikri temsil etmek amacıyla tasarlanmıştır.

Belirli bir niteliğe sahip metin ayarlamak için `bold`, `light`, `italic`, `underline`, `strikethrough` ve `inverse` yüzlerini kullanıyoruz.

16 terminal renkleri için ayrıca adlandırılmış yüzler de vardır: `siyah`, `kırmızı`, `yeşil`, `sarı`, `mavi`, `macenta`, `cyan`, `beyaz`, `parlak_siyah`/`gri`, `parlak_kırmızı`, `parlak_yeşil`, `parlak_mavi`, `parlak_macenta`, `parlak_cyan` ve `parlak_beyaz`.

Gölgelendirilmiş metin için (yani, soluk ama orada) `shadow` yüzü vardır. Seçili bir bölgeyi belirtmek için `region` yüzü vardır. Benzer şekilde, vurgulama ve öne çıkarma için `emphasis` ve `highlight` yüzleri tanımlanmıştır. Ayrıca, kod benzeri metinler için `code` de vardır.

Mesajların ciddiyetini görsel olarak belirtmek için `hata`, `uyarı`, `başarı`, `bilgi`, `not` ve `ipuçları` yüzleri tanımlanmıştır.

### [Customisation of faces (`Faces.toml`)](@id stdlib-styledstrings-face-toml)

Küresel yüz sözlüğündeki isim yüzlerinin özelleştirilebilir olması iyidir. Temalar ve estetikler hoş, ayrıca erişilebilirlik nedenleriyle de önemlidir. Bir TOML dosyası, yüz sözlüğündeki mevcut girişle birleştirilen [`Face`](@ref StyledStrings.Face) spesifikasyonları listesine ayrıştırılabilir.

Bir [`Face`](@ref StyledStrings.Face) TOML formatında şu şekilde temsil edilir:

```toml
[facename]
attribute = "value"
...

[package.facename]
attribute = "value"
```

Örneğin, eğer `gölge` yüzü okunması çok zor ise, şöyle daha parlak hale getirilebilir:

```toml
[shadow]
foreground = "white"
```

Başlatıldığında, ilk Julia depo altında bulunan `config/faces.toml` dosyası (genellikle `~/.julia`) yüklenir.

### Applying faces to a `AnnotatedString`

Gelenek gereği, [`AnnotatedString`](@ref Base.AnnotatedString)'nin `:face` nitelikleri, şu anda geçerli olan [`Face`](@ref StyledStrings.Face)'ler hakkında bilgi tutar. Bu, global yüz sözlüğündeki bir `Symbol` ile adlandırılan bir `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`, bir `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` veya bunların bir vektörü şeklinde birden fazla biçimde verilebilir.

`show(::IO, ::MIME"text/plain", ::AnnotatedString)` ve `show(::IO, ::MIME"text/html", ::AnnotatedString)` yöntemleri, genel stil belirlenirken `:face` niteliklerine bakar ve hepsini bir araya getirir.

`AnnotatedString` oluşturulurken `:face` niteliklerini sağlayabilir, bunları sonrasında özellikler listesine ekleyebilir veya kullanışlı [Styled String literals](@ref stdlib-styledstring-literals)'i kullanabilirsiniz.

```@repl demo
str1 = AnnotatedString("blue text", [(1:9, :face, :blue)])
str2 = styled"{blue:blue text}"
str1 == str2
sprint(print, str1, context = :color => true)
sprint(show, MIME("text/html"), str1, context = :color => true)
```

## [Styled String Literals](@id stdlib-styledstring-literals)

[`AnnotatedString`](@ref Base.AnnotatedString) ile [`Face`](@ref StyledStrings.Face)'lerin uygulanmasıyla, [`styled"..."`](@ref @styled_str) stilinde bir dize literal'i, içeriğin ve niteliklerin özel bir dil bilgisi aracılığıyla kolayca ifade edilmesine olanak tanır.

[`styled"..."`](@ref @styled_str) literal içinde, süslü parantezler normal kullanımda özel karakterler olarak kabul edilir ve kaçış karakteri ile kullanılmalıdır (`\{`, `\}`). Bu, (iç içe) `{annotations...:text}` yapıları ile notasyonları ifade etmek için kullanılmalarına olanak tanır.

`annotations...` bileşeni, üç tür anotasyonun virgülle ayrılmış bir listesidir.

  * Yüz isimleri
  * Satır içi `Yüz` ifadeleri `(anahtar=değer,...)`
  * `ana=değer` çiftleri

İnterpolasyon, yalnızca satır içi yüz anahtarları için mümkün değildir.

Daha fazla bilgi için, [`styled"..."`](@ref @styled_str) docstring'inin genişletilmiş yardımına bakın.

Örnek olarak, yukarıda bahsedilen yerleşik yüzlerin listesini şu şekilde gösterebiliriz:

```julia-repl
julia> println(styled"
The basic font-style attributes are {bold:bold}, {light:light}, {italic:italic},
{underline:underline}, and {strikethrough:strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:
 {black:■} {red:■} {green:■} {yellow:■} {blue:■} {magenta:■} {cyan:■} {white:■}
 {bright_black:■} {bright_red:■} {bright_green:■} {bright_yellow:■} {bright_blue:■} {bright_magenta:■} {bright_cyan:■} {bright_white:■}

Since {code:bright_black} is effectively grey, we define two aliases for it:
{code:grey} and {code:gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the
{code:inverse} face, for example: {magenta:some {inverse:inverse} text}.

The intent-based basic faces are {shadow:shadow} (for dim but visible text),
{region:region} for selections, {emphasis:emphasis}, and {highlight:highlight}.
As above, {code:code} is used for code-like text.

Lastly, we have the 'message severity' faces: {error:error}, {warning:warning},
{success:success}, {info:info}, {note:note}, and {tip:tip}.

Remember that all these faces (and any user or package-defined ones) can
arbitrarily nest and overlap, {region,tip:like {bold,italic:so}}.")
```

```@raw comment
Documenter doesn't properly represent all the styling above, so I've converted it manually to HTML and LaTeX.
```

```@raw html
<pre>
 The basic font-style attributes are <span style="font-weight: 700;">bold</span>, <span style="font-weight: 300;">light</span>, <span style="font-style: italic;">italic</span>,
 <span style="text-decoration: underline;">underline</span>, and <span style="text-decoration: line-through">strikethrough</span>.

 In terms of color, we have named faces for the 16 standard terminal colors:
  <span style="color: #1c1a23;">■</span> <span style="color: #a51c2c;">■</span> <span style="color: #25a268;">■</span> <span style="color: #e5a509;">■</span> <span style="color: #195eb3;">■</span> <span style="color: #803d9b;">■</span> <span style="color: #0097a7;">■</span> <span style="color: #dddcd9;">■</span>
  <span style="color: #76757a;">■</span> <span style="color: #ed333b;">■</span> <span style="color: #33d079;">■</span> <span style="color: #f6d22c;">■</span> <span style="color: #3583e4;">■</span> <span style="color: #bf60ca;">■</span> <span style="color: #26c6da;">■</span> <span style="color: #f6f5f4;">■</span>

 Since <span style="color: #0097a7;">bright_black</span> is effectively grey, we define two aliases for it:
 <span style="color: #0097a7;">grey</span> and <span style="color: #0097a7;">gray</span> to allow for regional spelling differences.

 To flip the foreground and background colors of some text, you can use the
 <span style="color: #0097a7;">inverse</span> face, for example: <span style="color: #803d9b;">some </span><span style="background-color: #803d9b;">inverse</span><span style="color: #803d9b;"> text</span>.

 The intent-based basic faces are <span style="color: #76757a;">shadow</span> (for dim but visible text),
 <span style="background-color: #3a3a3a;">region</span> for selections, <span style="color: #195eb3;">emphasis</span>, and <span style="background-color: #195eb3;">highlight</span>.
 As above, <span style="color: #0097a7;">code</span> is used for code-like text.

 Lastly, we have the 'message severity' faces: <span style="color: #ed333b;">error</span>, <span style="color: #e5a509;">warning</span>,
 <span style="color: #25a268;">success</span>, <span style="color: #26c6da;">info</span>, <span style="color: #76757a;">note</span>, and <span style="color: #33d079;">tip</span>.

 Remember that all these faces (and any user or package-defined ones) can
 arbitrarily nest and overlap, <span style="color: #33d079;background-color: #3a3a3a;">like <span style="font-weight: 700;font-style: italic;">so</span></span>.</pre>
```

```@raw latex
\begingroup
\ttfamily
\setlength{\parindent}{0pt}
\setlength{\parskip}{\baselineskip}

The basic font-style attributes are {\fontseries{b}\selectfont bold}, {\fontseries{l}\selectfont light}, {\fontshape{it}\selectfont italic},\\
\underline{underline}, and {strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:\\
{\color[HTML]{1c1a23}\(\blacksquare\)} {\color[HTML]{a51c2c}\(\blacksquare\)} {\color[HTML]{25a268}\(\blacksquare\)}
{\color[HTML]{e5a509}\(\blacksquare\)} {\color[HTML]{195eb3}\(\blacksquare\)} {\color[HTML]{803d9b}\(\blacksquare\)}
{\color[HTML]{0097a7}\(\blacksquare\)} {\color[HTML]{dddcd9}\(\blacksquare\)} \\
{\color[HTML]{76757a}\(\blacksquare\)} {\color[HTML]{ed333b}\(\blacksquare\)} {\color[HTML]{33d079}\(\blacksquare\)} {\color[HTML]{f6d22c}\(\blacksquare\)} {\color[HTML]{3583e4}\(\blacksquare\)} {\color[HTML]{bf60ca}\(\blacksquare\)} {\color[HTML]{26c6da}\(\blacksquare\)} {\color[HTML]{f6f5f4}\(\blacksquare\)}

Since {\color[HTML]{0097a7}bright\_black} is effectively grey, we define two aliases for it:\\
{\color[HTML]{0097a7}grey} and {\color[HTML]{0097a7}gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the\\
{\color[HTML]{0097a7}inverse} face, for example: {\color[HTML]{803d9b}some \colorbox[HTML]{803d9b}{\color[HTML]{000000}inverse} text}.

The intent-based basic faces are {\color[HTML]{76757a}shadow} (for dim but visible text),\\
\colorbox[HTML]{3a3a3a}{region} for selections, {\color[HTML]{195eb3}emphasis}, and \colorbox[HTML]{195eb3}{highlight}.\\
As above, {\color[HTML]{0097a7}code} is used for code-like text.

Lastly, we have the 'message severity' faces: {\color[HTML]{ed333b}error}, {\color[HTML]{e5a509}warning},\\
{\color[HTML]{25a268}success}, {\color[HTML]{26c6da}info}, {\color[HTML]{76757a}note}, and {\color[HTML]{33d079}tip}.

Remember that all these faces (and any user or package-defined ones) can\\
arbitrarily nest and overlap, \colorbox[HTML]{3a3a3a}{\color[HTML]{33d079}like
  {\fontseries{b}\fontshape{it}\selectfont so}}.
\endgroup
```

## [API reference](@id stdlib-styledstrings-api)

### Styling and Faces

```@docs
StyledStrings.@styled_str
StyledStrings.styled
StyledStrings.Face
StyledStrings.addface!
StyledStrings.withfaces
StyledStrings.SimpleColor
StyledStrings.parse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.tryparse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.merge(::StyledStrings.Face, ::StyledStrings.Face)
```
