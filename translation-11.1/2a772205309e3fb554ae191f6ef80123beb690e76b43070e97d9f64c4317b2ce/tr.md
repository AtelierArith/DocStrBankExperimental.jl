```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Markdown/docs/src/index.md"
```

# [Markdown](@id markdown_stdlib)

Bu bölüm, Markdown standart kütüphanesi tarafından etkinleştirilen Julia'nın markdown sözdizimini tanımlar. Aşağıdaki Markdown öğeleri desteklenmektedir:

## Inline elements

Burada "inline" terimi, metin blokları içinde, yani paragraflarda bulunabilen öğeleri ifade eder. Bunlar aşağıdaki öğeleri içerir.

### Bold

Kelimeleri iki yıldız işaretiyle, `**`, çevreleyerek içerideki metni kalın yazı ile görüntüleyin.

```
A paragraph containing a **bold** word.
```

### Italics

Kelimeleri italik olarak göstermek için bir yıldız işaretiyle, `*`, çevreleyin.

```
A paragraph containing an *italicized* word.
```

### Literals

Metin, tam olarak yazıldığı gibi görüntülenmesi gereken yerleri tek tırnaklı geri tırnak işaretiyle çevreleyin, ``` ` ``` .

```
A paragraph containing a `literal` word.
```

Değişkenlerin, fonksiyonların veya bir Julia programının diğer parçalarının adlarına atıfta bulunurken metin yazarken literal'lar kullanılmalıdır.

!!! tip
    Üç tırnak işareti kullanarak metin içinde bir ters tırnak karakteri eklemek için, metni sarmak için bir tane yerine üç tırnak işareti kullanın.

    ```
    A paragraph containing ``` `backtick` characters ```.
    ```

    Herhangi bir tek sayıda ters tırnak, daha az sayıda ters tırnağı kapsamak için kullanılabilir.


### $\LaTeX$

Metin, matematik olarak görüntülenmesi gereken yerleri, çift ters eğik çizgi ile `$ \LaTeX $` sözdizimi ile çevreleyin, ``` `` ```.

```
A paragraph containing some ``\LaTeX`` markup.
```

!!! tip
    Önceki bölümdeki literallerde olduğu gibi, eğer çift ters tırnak içinde yazılması gereken ters tırnaklar varsa, iki sayının daha büyük bir çift sayısını kullanın. Tek bir ters tırnağın $\LaTeX$ işaretlemesi içinde yer alması gerekiyorsa, iki çevreleyen ters tırnak yeterlidir.


!!! note
    `\\` karakteri, metin bir Julia kaynak koduna gömülü olduğunda uygun şekilde kaçırılmalıdır, örneğin, ```"``\\LaTeX`` bir docstring içindeki sözdizimi."```, çünkü bir dize literal olarak yorumlanır. Alternatif olarak, kaçırmayı önlemek için `@doc` makrosuyla birlikte `raw` dize makrosunu kullanmak mümkündür:

    ```
    @doc raw"``\LaTeX`` syntax in a docstring." functionname
    ```


### Links

Bağlantılar, dış veya iç hedeflere aşağıdaki sözdizimi kullanılarak yazılabilir; köşeli parantezler içinde yer alan metin, `[ ]`, bağlantının adıdır ve parantezler içinde yer alan metin, `( )`, URL'dir.

```
A paragraph containing a link to [Julia](https://www.julialang.org).
```

Julia belgelen belgesinde diğer belgelenmiş fonksiyonlara/yöntemlere/değişkenlere çapraz referanslar eklemek de mümkündür. Örneğin:

```julia
"""
    tryparse(type, str; base)

Like [`parse`](@ref), but returns either a value of the requested type,
or [`nothing`](@ref) if the string does not contain a valid number.
"""
```

Bu, oluşturulan belgelerde [`parse`](@ref) belgesine (bu işlevin gerçekten ne yaptığı hakkında daha fazla bilgi içeren) ve [`nothing`](@ref) belgesine bir bağlantı oluşturacaktır. Bir işlevin değiştiren/değiştirmeyen sürümleri arasında çapraz referanslar eklemek veya iki benzer görünen işlev arasındaki bir farkı vurgulamak iyi bir fikirdir.

!!! note
    Yukarıdaki çapraz referans *Markdown* özelliği değildir ve [Documenter.jl](https://github.com/JuliaDocs/Documenter.jl) kullanılarak oluşturulan temel Julia belgelerini inşa etmek için kullanılır.


### Footnote references

Adlandırılmış ve numaralandırılmış dipnot referansları aşağıdaki sözdizimi kullanılarak yazılabilir. Bir dipnot adı, noktalama işareti içermeyen tek bir alfanümerik kelime olmalıdır.

```
A paragraph containing a numbered footnote [^1] and a named one [^named].
```

!!! note
    Dipnotla ilişkili metin, dipnot referansının bulunduğu sayfanın herhangi bir yerinde yazılabilir. Dipnot metnini tanımlamak için kullanılan sözdizimi, aşağıdaki [Footnotes](@ref) bölümünde tartışılmaktadır.


## Toplevel elements

Aşağıdaki öğeler, bir belgenin "üst düzey" kısmında veya başka bir "üst düzey" öğenin içinde yazılabilir.

### Paragraphs

Bir paragraf, yukarıdaki [Inline elements](@ref) bölümünde tanımlanan herhangi bir sayıda satır içi öğe içerebilen, bir veya daha fazla boş satırla yukarıda ve aşağıda yer alan düz metin bloğudur.

```
This is a paragraph.

And this is *another* paragraph containing some emphasized text.
A new line, but still part of the same paragraph.
```

### Headers

Bir belge, başlıklar kullanılarak farklı bölümlere ayrılabilir. Başlıklar aşağıdaki sözdizimini kullanır:

```julia
# Level One
## Level Two
### Level Three
#### Level Four
##### Level Five
###### Level Six
```

Bir başlık satırı, bir paragrafın yapabileceği gibi herhangi bir satır içi sözdizimini içerebilir.

!!! tip
    Tek bir belgede çok fazla başlık seviyesi kullanmaktan kaçının. Aşırı derecede iç içe geçmiş bir belge, onu yeniden yapılandırma veya ayrı konuları kapsayan birkaç sayfaya ayırma ihtiyacını gösterebilir.


### Code blocks

Kaynak kodu, aşağıdaki örnekte gösterildiği gibi, dört boşluk veya bir sekme ile girilerek bir literal blok olarak görüntülenebilir.

```
This is a paragraph.

    function func(x)
        # ...
    end

Another paragraph.
```

Ayrıca, kod blokları, bir kod bloğunun nasıl vurgulanacağını belirtmek için isteğe bağlı bir "dil" ile birlikte üçlü ters tırnak işareti kullanılarak kapatılabilir.

````
A code block without a "language":

```
function func(x)
    # ...
end
```

and another one with the "language" specified as `julia`:

```julia
function func(x)
    # ...
end
```
````

!!! note
    "Fenced" kod blokları, son örnekte gösterildiği gibi, girintili kod bloklarına göre tercih edilmelidir çünkü girintili kod bloklarının hangi dilde yazıldığını belirtmenin bir yolu yoktur.


### Block quotes

Dış kaynaklardan alınan metinler, alıntı yapmak için her bir satırın başına `>` karakterleri eklenerek aşağıdaki gibi gösterilebilir.

```
Here's a quote:

> Julia is a high-level, high-performance dynamic programming language for
> technical computing, with syntax that is familiar to users of other
> technical computing environments.
```

Markdown.Paragraph(Any["Not edin ki, her satırda ", Markdown.Code("", ">"), " karakterinden sonra bir boşluk olmalıdır. Alıntı blokları kendileri de diğer üst düzey veya satır içi öğeleri içerebilir."])

### Images

Görüntüler için sözdizimi, yukarıda bahsedilen bağlantı sözdizimine benzer. Bir bağlantının önüne `!` karakteri eklemek, belirtilen URL'den bir görüntü gösterecek, ona bir bağlantı yerine.

```julia
![alternative text](link/to/image.png)
```

### Lists

Sırasız listeler, bir listedeki her öğenin önüne `*`, `+` veya `-` eklenerek yazılabilir.

```
A list of items:

  * item one
  * item two
  * item three
```

Not edin iki boşluk her `*` öncesinde ve her birinin ardından bir boşluk.

Listeler, listeler, kod blokları veya alıntı blokları gibi diğer iç içe geçmiş üst düzey öğeleri içerebilir. Bir liste içinde herhangi bir üst düzey öğe içerdiğinde, her liste öğesi arasında boş bir satır bırakılmalıdır.

```
Another list:

  * item one

  * item two

    ```
    f(x) = x
    ```

  * And a sublist:

      + sub-item one
      + sub-item two
```

!!! note
    Her listedeki her bir öğenin içeriği, öğenin ilk satırıyla hizalanmalıdır. Yukarıdaki örnekte, fenced kod bloğu `item two`daki `i` ile hizalanmak için dört boşlukla girintilenmelidir.


Sıralı listeler, "madde" karakterini, `*`, `+` veya `-` yerine pozitif bir tam sayı ile ardından ya `.` ya da `)` ekleyerek yazılır.

```
Two ordered lists:

 1. item one
 2. item two
 3. item three

 5) item five
 6) item six
 7) item seven
```

Sıralı bir liste, yukarıdaki örnekteki ikinci listede olduğu gibi, birden başka bir sayıdan başlayabilir; burada beşten numaralandırılmıştır. Sırasız listelerde olduğu gibi, sıralı listeler de iç içe geçmiş üst düzey öğeler içerebilir.

### Display equations

Büyük $\LaTeX$ denklemleri bir paragraf içinde satır içi olarak yer almadığında, aşağıdaki örnekte olduğu gibi "dil" `math` olan bir fenced kod bloğu kullanarak gösterilebilir.

````julia
```math
f(a) = \frac{1}{2\pi}\int_{0}^{2\pi} (\alpha+R\cos(\theta))d\theta
```
````

### Footnotes

Bu sözdizimi, [Footnote references](@ref) için satır içi sözdizimi ile eşleştirilmiştir. O bölümü de okuduğunuzdan emin olun.

Dipnot metni, dipnot referans sözdizimine benzer olan aşağıdaki sözdizimi kullanılarak tanımlanır; tek fark, dipnot etiketine eklenen `:` karakteridir.

```
[^1]: Numbered footnote text.

[^note]:

    Named footnote text containing several toplevel elements
    indented by 4 spaces or one tab.

      * item one
      * item two
      * item three

    ```julia
    function func(x)
        # ...
    end
    ```
```

!!! note
    Parçalama sırasında tüm dipnot referanslarının eşleşen dipnotlara sahip olduğundan emin olmak için hiçbir kontrol yapılmaz.


### Horizontal rules

Üç tire (`---`) kullanarak bir `<hr>` HTML etiketinin eşdeğerini elde edebilirsiniz. Örneğin:

```
Text above the line.

---

And text below the line.
```

### Tables

Temel tablolar aşağıda açıklanan sözdizimi kullanılarak yazılabilir. Markdown tablolarının sınırlı özellikleri vardır ve yukarıda tartışılan diğer öğeler gibi iç içe üst düzey öğeler içeremez - yalnızca satır içi öğelere izin verilir. Tablolar her zaman sütun adlarıyla bir başlık satırı içermelidir. Hücreler tablonun birden fazla satırını veya sütununu kapsayamaz.

```
| Column One | Column Two | Column Three |
|:---------- | ---------- |:------------:|
| Row `1`    | Column `2` |              |
| *Row* 2    | **Row** 2  | Column ``3`` |
```

!!! note
    Yukarıdaki örnekte gösterildiği gibi, her `|` karakteri sütunu dikey olarak hizalanmalıdır.

    Bir sütun başlığı ayırıcılarının ( `-` karakterlerini içeren satır) her iki ucundaki `:` karakteri, satırın sola, sağa veya (her iki uçta `:` olduğunda) ortalanmış olarak hizalanıp hizalanmayacağını belirtir. `:` karakteri sağlanmadığında, sütun sağa hizalanır.


### Admonitions

Özel olarak biçimlendirilmiş bloklar, belirli yorumları vurgulamak için kullanılabilen uyarılar olarak bilinir. Aşağıdaki `!!!` sözdizimini kullanarak tanımlanabilirler:

```
!!! note

    This is the content of the note.
    It is indented by 4 spaces. A tab would work as well.

!!! warning "Beware!"

    And this is another one.

    This warning admonition has a custom title: `"Beware!"`.
```

`!!!` sonrasındaki ilk kelime, uyarının türünü belirtir. Özel stil uygulaması gereken standart uyarı türleri vardır. Bunlar (ciddiyet sırasına göre azalan): `tehlike`, `uyarı`, `bilgi`/`not` ve `ipuçları`.

Kendi uyarı türlerinizi de kullanabilirsiniz, yeter ki tür adı yalnızca küçük Latin harfleri (a-z) içersin. Örneğin, şöyle bir `terminology` bloğunuz olabilir:

```
!!! terminology "julia vs Julia"

    Strictly speaking, "Julia" refers to the language,
    and "julia" to the standard implementation.
```

Ancak, Markdown'u işleyen kod o belirli uyarı türünü özel olarak ele almadıkça, varsayılan stil alacaktır.

Bir kutu için özel bir başlık, uyarı türünden sonra bir dize (çift tırnak içinde) olarak sağlanabilir. Eğer uyarı türünden sonra başlık metni belirtilmemişse, o zaman başlık olarak tür adı kullanılacaktır (örneğin, `note` uyarısı için `"Not"`).

Uyarılar, diğer çoğu üst düzey öğe gibi, diğer üst düzey öğeleri (örneğin listeler, resimler) içerebilir.

## [Markdown String Literals](@id stdlib-markdown-literals)

`md""` makrosu, Markdown dizelerini doğrudan Julia kodunuza yerleştirmenizi sağlar. Bu makro, Markdown formatında metinlerin Julia kaynak dosyalarınıza dahil edilmesini basitleştirmek için tasarlanmıştır.

### Usage

```julia
result = md"This is a **custom** Markdown string with [a link](http://example.com)."
```

## Markdown Syntax Extensions

Julia'nın markdown'u, temel dize literallerine çok benzer bir şekilde interpolasyonu destekler; farkı, nesneyi Markdown ağacında saklamasıdır (onu bir dizeye dönüştürmek yerine). Markdown içeriği render edildiğinde, genellikle `show` yöntemleri çağrılacaktır ve bunlar her zamanki gibi geçersiz kılınabilir. Bu tasarım, temel sözdizimini karmaşık özelliklerle (referanslar gibi) karıştırmadan genişletmeye olanak tanır.

Prensip olarak, Markdown ayrıştırıcısı kendisi de paketler tarafından keyfi olarak genişletilebilir veya tamamen özel bir Markdown çeşidi kullanılabilir, ancak bu genellikle gereksiz olmalıdır.

## [API reference](@id stdlib-markdown-api)

```@docs
Markdown.MD
Markdown.@md_str
Markdown.@doc_str
Markdown.html
Markdown.latex
```
