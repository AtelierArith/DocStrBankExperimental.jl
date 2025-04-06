# [Getting Started](@id man-getting-started)

Julia kurulumu, önceden derlenmiş ikili dosyalar kullanarak veya kaynak kodundan derleyerek oldukça basittir. Julia'yı indirin ve kurun, talimatları izleyerek [https://julialang.org/downloads/](https://julialang.org/downloads/) adresinde bulabilirsiniz.

Eğer Julia'ya aşağıdaki dillerden birinden geliyorsanız, [MATLAB](@ref Noteworthy-differences-from-MATLAB), [R](@ref Noteworthy-differences-from-R), [Python](@ref Noteworthy-differences-from-Python), [C/C++](@ref Noteworthy-differences-from-C/C) veya [Common Lisp](@ref Noteworthy-differences-from-Common-Lisp) bölümünü okumaya başlamalısınız. Bu, Julia'nın bu dillerden birçok ince noktada farklılık gösterdiği için bazı yaygın tuzaklardan kaçınmanıza yardımcı olacaktır.

Julia'yı öğrenmenin ve denemenin en kolay yolu, Julia yürütülebilir dosyasına çift tıklayarak veya komut satırından `julia` yazarak etkileşimli bir oturum (aynı zamanda okuma-değerlendirme-yazdırma döngüsü veya "REPL" olarak da bilinir) başlatmaktır:

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia> 1 + 2\n3\n\njulia> ans\n3\n```")
```

Etkileşimli oturumu kapatmak için `CTRL-D` yazın (Control/`^` tuşuna `d` tuşu ile birlikte basın) veya `exit()` yazın. Etkileşimli modda çalıştırıldığında, `julia` bir afiş gösterir ve kullanıcıdan girdi ister. Kullanıcı, `1 + 2` gibi tamamlanmış bir ifade girdikten ve enter tuşuna bastıktan sonra, etkileşimli oturum ifadeyi değerlendirir ve değerini gösterir. Bir etkileşimli oturuma bir ifade, sonuna noktalı virgül eklenerek girildiğinde, değeri gösterilmez. `ans` değişkeni, gösterilip gösterilmediğine bakılmaksızın son değerlendirilen ifadenin değerine bağlanır. `ans` değişkeni yalnızca etkileşimli oturumlarda bağlanır, Julia kodu başka şekillerde çalıştırıldığında değil.

Bir kaynak dosyasında yazılmış ifadeleri değerlendirmek için `include("file.jl")` yazın.

Bir dosyada kodu etkileşimsiz olarak çalıştırmak için, bunu `julia` komutuna birinci argüman olarak verebilirsiniz:

```
$ julia script.jl
```

Julia'ya ve programınıza `script.jl` ek argümanlar geçirebilirsiniz. Tüm mevcut seçeneklerin ayrıntılı bir listesi [Command-line Interface](@ref cli) altında bulunabilir.

## Resources

Yeni kullanıcıların başlamalarına yardımcı olacak yararlı öğrenme kaynaklarının derlenmiş bir listesi, ana Julia web sitesinin [learning](https://julialang.org/learning/) sayfasında bulunabilir.

REPL'i bir öğrenme kaynağı olarak kullanabilirsiniz, yardım moduna geçerek. Yardım moduna geçmek için, başka bir şey yazmadan önce boş bir `julia>` isteminde `?` tuşuna basın. Yardım modunda bir anahtar kelime yazmak, onunla ilgili belgeleri ve örnekleri getirir. Benzer şekilde, karşılaşabileceğiniz çoğu fonksiyon veya diğer nesneler için de geçerlidir!

```
help?> begin
search: begin disable_sigint reenable_sigint

  begin

  begin...end denotes a block of code.
```

Eğer biraz Julia biliyorsanız, [Performance Tips](@ref man-performance-tips) ve [Workflow Tips](@ref man-workflow-tips)'e göz atmak isteyebilirsiniz.
