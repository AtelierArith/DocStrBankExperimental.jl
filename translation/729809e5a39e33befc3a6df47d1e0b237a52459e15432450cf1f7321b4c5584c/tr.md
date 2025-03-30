```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/REPL/docs/src/index.md"
```

# The Julia REPL

Julia, `julia` yürütülebilir dosyasına entegre edilmiş tam özellikli etkileşimli komut satırı REPL (okuma-değerlendirme-yazdırma döngüsü) ile birlikte gelir. Julia ifadelerinin hızlı ve kolay bir şekilde değerlendirilmesine olanak tanımanın yanı sıra, arama yapılabilir bir geçmiş, sekme tamamlama, birçok yararlı tuş ataması ve özel yardım ve kabuk modları içerir. REPL, yalnızca `julia` çağrılarak veya yürütülebilir dosyaya çift tıklanarak başlatılabilir:

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia>\n```")
```

Etkileşimli oturumu kapatmak için, boş bir satıra `^D` yazın – kontrol tuşu ile `d` tuşunu birlikte basın – veya `exit()` yazıp ardından geri dönüş veya enter tuşuna basın. REPL, sizi bir afiş ve `julia>` istemi ile karşılar.

## The different prompt modes

### The Julian mode

REPL'in beş ana çalışma modu vardır. İlk ve en yaygın olanı Julian istemidir. Bu, varsayılan çalışma modudur; her yeni satır başlangıçta `julia>` ile başlar. Burada Julia ifadelerini girebilirsiniz. Tam bir ifade girildikten sonra return veya enter tuşuna basmak, girişi değerlendirir ve son ifadenin sonucunu gösterir.

```jldoctest
julia> string(1 + 2)
"3"
```

Etkileşimli çalışmaya özgü bir dizi yararlı özellik vardır. Sonucu göstermekle birlikte, REPL aynı zamanda sonucu `ans` değişkenine bağlar. Satırın sonundaki bir noktalı virgül, sonucu göstermeyi bastırmak için bir bayrak olarak kullanılabilir.

```jldoctest
julia> string(3 * 4);

julia> ans
"12"
```

Julia modunda, REPL, *prompt pasting* adı verilen bir şeyi destekler. Bu, REPL'ye `julia>` ile başlayan metin yapıştırıldığında etkinleşir. Bu durumda, yalnızca `julia>` ile başlayan ifadeler (ve diğer REPL mod istemleri: `shell>`, `help?>`, `pkg>` ) ayrıştırılır, ancak diğerleri kaldırılır. Bu, bir REPL oturumundan kopyalanmış bir metin parçasını, istemleri ve çıktıları temizlemeden yapıştırmayı mümkün kılar. Bu özellik varsayılan olarak etkindir ancak `REPL.enable_promptpaste(::Bool)` ile istenildiği gibi devre dışı bırakılabilir veya etkinleştirilebilir. Eğer etkinse, bu paragrafın üstündeki kod bloğunu doğrudan REPL'ye yapıştırarak deneyebilirsiniz. Bu özellik, bir yapıştırma işleminin gerçekleştiğini algılama konusundaki sınırlamaları nedeniyle standart Windows komut istemcisinde çalışmaz.

Objects are printed at the REPL using the [`show`](@ref) function with a specific [`IOContext`](@ref). In particular, the `:limit` attribute is set to `true`. Other attributes can receive in certain `show` methods a default value if it's not already set, like `:compact`. It's possible, as an experimental feature, to specify the attributes used by the REPL via the `Base.active_repl.options.iocontext` dictionary (associating values to attributes). For example:

```julia-repl
julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.8833    0.329197
 0.719708  0.59114

julia> show(IOContext(stdout, :compact => false), "text/plain", rand(2, 2))
 0.43540323669187075  0.15759787870609387
 0.2540832269192739   0.4597637838786053
julia> Base.active_repl.options.iocontext[:compact] = false;

julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.2083967319174056  0.13330606013126012
 0.6244375177790158  0.9777957560761545
```

Başlangıç zamanında bu sözlüğün değerlerini otomatik olarak tanımlamak için, `~/.julia/config/startup.jl` dosyasında [`atreplinit`](@ref) fonksiyonunu kullanabilirsiniz, örneğin:

```julia
atreplinit() do repl
    repl.options.iocontext[:compact] = false
end
```

### Help mode

İmleç satırın başındayken, istemci `?` yazarak yardım moduna geçebilir. Julia, yardım modunda girilen her şey için yardım veya belgeleri yazdırmaya çalışacaktır:

```julia-repl
julia> ? # upon typing ?, the prompt changes (in place) to: help?>

help?> string
search: string String Cstring Cwstring RevString randstring bytestring SubString

  string(xs...)

  Create a string from any values using the print function.
```

Makrolar, türler ve değişkenler de sorgulanabilir:

```
help?> @time
  @time

  A macro to execute an expression, printing the time it took to execute, the number of allocations,
  and the total number of bytes its execution caused to be allocated, before returning the value of the
  expression.

  See also @timev, @timed, @elapsed, and @allocated.

help?> Int32
search: Int32 UInt32

  Int32 <: Signed

  32-bit signed integer type.
```

Bir dize veya regex literali, tüm belge dizelerini [`apropos`](@ref) kullanarak arar:

```
help?> "aprop"
REPL.stripmd
Base.Docs.apropos

help?> r"ap..p"
Base.:∘
Base.shell_escape_posixly
Distributed.CachingPool
REPL.stripmd
Base.Docs.apropos
```

Yardım modunun bir diğer özelliği, genişletilmiş doküman dizelerine erişimdir. Bunu `?Print` yerine `??Print` yazarak yapabilirsiniz; bu, kaynak kodlarının belgelerinden `# Genişletilmiş yardım` bölümünü görüntüler.

Yardım modu, satırın başında backspace tuşuna basarak çıkılabilir.

### [Shell mode](@id man-shell-mode)

Yardım modu, belgelere hızlı erişim için yararlı olduğu gibi, başka bir yaygın görev de sistem komutlarını yürütmek için sistem kabuğunu kullanmaktır. Satırın başında `?` girildiğinde yardım moduna geçildiği gibi, bir noktalı virgül (`;`) kabuk moduna geçecektir. Ve satırın başında backspace tuşuna basarak çıkılabilir.

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> echo hello
hello
```

!!! note
    Windows kullanıcıları için, Julia'nın shell modu Windows shell komutlarını açmaz. Bu nedenle, bu başarısız olacaktır:


```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> dir
ERROR: IOError: could not spawn `dir`: no such file or directory (ENOENT)
Stacktrace!
.......
```

Ancak, `PowerShell`'a bu şekilde erişim sağlayabilirsiniz:

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.
PS C:\Users\elm>
```

... ve `cmd.exe` böyle (bkz. `dir` komutu):

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> cmd
Microsoft Windows [version 10.0.17763.973]
(c) 2018 Microsoft Corporation. All rights reserved.
C:\Users\elm>dir
 Volume in drive C has no label
 Volume Serial Number is 1643-0CD7
  Directory of C:\Users\elm

29/01/2020  22:15    <DIR>          .
29/01/2020  22:15    <DIR>          ..
02/02/2020  08:06    <DIR>          .atom
```

### Pkg mode

Paket yöneticisi modu, paketleri yüklemek ve güncellemek için özel komutları kabul eder. Bu moda, Julian REPL istemcisinde `]` tuşuna basarak girilir ve CTRL-C tuşuna basarak veya satırın başında backspace tuşuna basarak çıkılır. Bu modun istemcisi `pkg>` şeklindedir. Kendi yardım modunu destekler; bu mod, `pkg>` istemcisinin satırının başında `?` tuşuna basarak girilir. Paket yöneticisi modu, [https://julialang.github.io/Pkg.jl/v1/](https://julialang.github.io/Pkg.jl/v1/) adresinde bulunan Pkg kılavuzunda belgelenmiştir.

### Search modes

Yukarıdaki tüm modlarda, yürütülen satırlar bir geçmiş dosyasına kaydedilir ve bu dosya aranabilir. Önceki geçmişte artımlı bir arama başlatmak için `^R` tuşlarına basın - kontrol tuşu ile `r` tuşunu birlikte kullanın. İstemci, ```(reverse-i-search)`':``` şeklinde değişecektir ve arama sorgusunu yazdıkça tırnak içinde görünecektir. Sorguyla eşleşen en son sonuç, daha fazla yazıldıkça iki nokta üst üste işaretinin sağında dinamik olarak güncellenecektir. Aynı sorguyu kullanarak daha eski bir sonucu bulmak için, sadece `^R` tuşlarına tekrar basın.

Tam `^R` ters arama ise, `^S` ileri arama olup, istemci ```(i-search)`':```. İkisi, sırasıyla önceki veya sonraki eşleşen sonuçlar arasında geçiş yapmak için bir arada kullanılabilir.

Tüm yürütülen komutlar Julia REPL'inde `~/.julia/logs/repl_history.jl` dosyasına kaydedilir; bu dosya, komutun yürütüldüğü zaman damgasını ve bulunduğunuz mevcut REPL modunu içerir. Arama modu, daha önce çalıştırdığınız komutları bulmak için bu günlük dosyasını sorgular. Bu, Julia'ya `--history-file=no` bayrağını geçirerek başlangıçta devre dışı bırakılabilir.

## Key bindings

Julia REPL, tuş bağlamalarını etkili bir şekilde kullanır. Daha önce tanıtılan birkaç kontrol tuşu bağlaması (`^D` çıkmak için, `^R` ve `^S` arama için) vardı, ancak daha birçok bağlama bulunmaktadır. Kontrol tuşuna ek olarak, meta tuş bağlamaları da vardır. Bunlar platforma göre daha fazla değişiklik gösterir, ancak çoğu terminal, meta tuşunu göndermek için bir tuşla birlikte basılı tutulan alt veya seçenek tuşunu kullanmayı varsayılan olarak ayarlar (veya bunu yapılandırmak mümkündür) veya önce Esc tuşuna basıp ardından tuşa basarak kullanılır.

| Keybinding           | Description                                                                                                |
|:-------------------- |:---------------------------------------------------------------------------------------------------------- |
| **Program control**  |                                                                                                            |
| `^D`                 | Exit (when buffer is empty)                                                                                |
| `^C`                 | Interrupt or cancel                                                                                        |
| `^L`                 | Clear console screen                                                                                       |
| Return/Enter, `^J`   | New line, executing if it is complete                                                                      |
| meta-Return/Enter    | Insert new line without executing it                                                                       |
| `?` or `;`           | Enter help or shell mode (when at start of a line)                                                         |
| `^R`, `^S`           | Incremental history search, described above                                                                |
| **Cursor movement**  |                                                                                                            |
| Right arrow, `^F`    | Move right one character                                                                                   |
| Left arrow, `^B`     | Move left one character                                                                                    |
| ctrl-Right, `meta-F` | Move right one word                                                                                        |
| ctrl-Left, `meta-B`  | Move left one word                                                                                         |
| Home, `^A`           | Move to beginning of line                                                                                  |
| End, `^E`            | Move to end of line                                                                                        |
| Up arrow, `^P`       | Move up one line (or change to the previous history entry that matches the text before the cursor)         |
| Down arrow, `^N`     | Move down one line (or change to the next history entry that matches the text before the cursor)           |
| Shift-Arrow Key      | Move cursor according to the direction of the Arrow key, while activating the region ("shift selection")   |
| Page-up, `meta-P`    | Change to the previous history entry                                                                       |
| Page-down, `meta-N`  | Change to the next history entry                                                                           |
| `meta-<`             | Change to the first history entry (of the current session if it is before the current position in history) |
| `meta->`             | Change to the last history entry                                                                           |
| `^-Space`            | Set the "mark" in the editing region (and de-activate the region if it's active)                           |
| `^-Space ^-Space`    | Set the "mark" in the editing region and make the region "active", i.e. highlighted                        |
| `^G`                 | De-activate the region (i.e. make it not highlighted)                                                      |
| `^X^X`               | Exchange the current position with the mark                                                                |
| **Editing**          |                                                                                                            |
| Backspace, `^H`      | Delete the previous character, or the whole region when it's active                                        |
| Delete, `^D`         | Forward delete one character (when buffer has text)                                                        |
| meta-Backspace       | Delete the previous word                                                                                   |
| `meta-d`             | Forward delete the next word                                                                               |
| `^W`                 | Delete previous text up to the nearest whitespace                                                          |
| `meta-w`             | Copy the current region in the kill ring                                                                   |
| `meta-W`             | "Kill" the current region, placing the text in the kill ring                                               |
| `^U`                 | "Kill" to beginning of line, placing the text in the kill ring                                             |
| `^K`                 | "Kill" to end of line, placing the text in the kill ring                                                   |
| `^Y`                 | "Yank" insert the text from the kill ring                                                                  |
| `meta-y`             | Replace a previously yanked text with an older entry from the kill ring                                    |
| `^T`                 | Transpose the characters about the cursor                                                                  |
| `meta-Up arrow`      | Transpose current line with line above                                                                     |
| `meta-Down arrow`    | Transpose current line with line below                                                                     |
| `meta-u`             | Change the next word to uppercase                                                                          |
| `meta-c`             | Change the next word to titlecase                                                                          |
| `meta-l`             | Change the next word to lowercase                                                                          |
| `^/`, `^_`           | Undo previous editing action                                                                               |
| `^Q`                 | Write a number in REPL and press `^Q` to open editor at corresponding stackframe or method                 |
| `meta-Left Arrow`    | Indent the current line on the left                                                                        |
| `meta-Right Arrow`   | Indent the current line on the right                                                                       |
| `meta-.`             | Insert last word from previous history entry                                                               |
| `meta-e`             | Edit the current input in an editor                                                                        |

### Customizing keybindings

Julia'nın REPL kısayolları, `REPL.setup_interface` fonksiyonuna bir sözlük geçirerek bir kullanıcının tercihlerine tamamen özelleştirilebilir. Bu sözlüğün anahtarları karakterler veya dizeler olabilir. Anahtar `'*'`, varsayılan eylemi ifade eder. Kontrol artı karakter `x` kısayolları `"^x"` ile gösterilir. Meta artı `x`, `"\\M-x"` veya `"\ex"` olarak yazılabilir, ve Kontrol artı `x` `"\\C-x"` veya `"^x"` olarak yazılabilir. Özel kısayol haritasının değerleri `nothing` (girişin yok sayılmasını belirtir) veya `(PromptState, AbstractREPL, Char)` imzasını kabul eden fonksiyonlar olmalıdır. `REPL.setup_interface` fonksiyonu, REPL başlatılmadan önce çağrılmalı ve işlem [`atreplinit`](@ref) ile kaydedilmelidir. Örneğin, yukarı ve aşağı ok tuşlarını geçmişte gezinmek için ön ek arama olmadan bağlamak için, aşağıdaki kod `~/.julia/config/startup.jl` dosyasına konulabilir:

```julia
import REPL
import REPL.LineEdit

const mykeys = Dict{Any,Any}(
    # Up Arrow
    "\e[A" => (s,o...)->(LineEdit.edit_move_up(s) || LineEdit.history_prev(s, LineEdit.mode(s).hist)),
    # Down Arrow
    "\e[B" => (s,o...)->(LineEdit.edit_move_down(s) || LineEdit.history_next(s, LineEdit.mode(s).hist))
)

function customize_keys(repl)
    repl.interface = REPL.setup_interface(repl; extra_repl_keymap = mykeys)
end

atreplinit(customize_keys)
```

Kullanıcılar, tuş girişi üzerindeki mevcut eylemleri keşfetmek için `LineEdit.jl`'ye başvurmalıdır.

## Tab completion

Julian, pkg ve yardım modlarında REPL'de, bir fonksiyonun veya tipin ilk birkaç karakterini girebilir ve ardından tüm eşleşmeleri listelemek için tab tuşuna basabilirsiniz:

```julia-repl
julia> x[TAB]
julia> xor
```

Bazen yalnızca ismin bir kısmını, bir sonraki belirsizliğe kadar tamamlar:

```julia-repl
julia> mapf[TAB]
julia> mapfold
```

Eğer tekrar tab tuşuna basarsanız, bu durumu tamamlayabilecek şeylerin listesini alırsınız:

```julia-repl
julia> mapfold[TAB]
mapfoldl mapfoldr
```

Bir giriş satırının sonunda tek bir tamamlanmış tab-tamamla sonucu mevcut olduğunda ve 2 veya daha fazla karakter yazıldığında, tamamlamanın bir ipucu daha açık bir renkte gösterilecektir. Bu, `Base.active_repl.options.hint_tab_completes = false` ile devre dışı bırakılabilir.

!!! compat "Julia 1.11"
    Tab-tamamlama ipuçları Julia 1.11'de eklendi.


REPL'in diğer bileşenleri gibi, arama büyük/küçük harf duyarlıdır:

```julia-repl
julia> stri[TAB]
stride     strides     string      strip

julia> Stri[TAB]
StridedArray    StridedMatrix    StridedVecOrMat  StridedVector    String
```

Tab tuşu, LaTeX matematik sembollerini Unicode eşdeğerleriyle değiştirmek ve LaTeX eşleşmelerinin bir listesini almak için de kullanılabilir:

```julia-repl
julia> \pi[TAB]
julia> π
π = 3.1415926535897...

julia> e\_1[TAB] = [1,0]
julia> e₁ = [1,0]
2-element Array{Int64,1}:
 1
 0

julia> e\^1[TAB] = [1 0]
julia> e¹ = [1 0]
1×2 Array{Int64,2}:
 1  0

julia> \sqrt[TAB]2     # √ is equivalent to the sqrt function
julia> √2
1.4142135623730951

julia> \hbar[TAB](h) = h / 2\pi[TAB]
julia> ħ(h) = h / 2π
ħ (generic function with 1 method)

julia> \h[TAB]
\hat              \hermitconjmatrix  \hkswarow          \hrectangle
\hatapprox        \hexagon           \hookleftarrow     \hrectangleblack
\hbar             \hexagonblack      \hookrightarrow    \hslash
\heartsuit        \hksearow          \house             \hspace

julia> α="\alpha[TAB]"   # LaTeX completion also works in strings
julia> α="α"
```

Tamam bir liste tab-tamamlamalar [Unicode Input](@ref) bölümünde kılavuzda bulunabilir.

Tamamlanma yolları, dizeler ve Julia'nın kabuk modunda çalışır:

```julia-repl
julia> path="/[TAB]"
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
shell> /[TAB]
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
```

Sözlük anahtarları da sekme ile tamamlanabilir:

```julia-repl
julia> foo = Dict("qwer1"=>1, "qwer2"=>2, "asdf"=>3)
Dict{String,Int64} with 3 entries:
  "qwer2" => 2
  "asdf"  => 3
  "qwer1" => 1

julia> foo["q[TAB]

"qwer1" "qwer2"
julia> foo["qwer
```

Tamamlanmış alanları tamamlamaya yardımcı olmak için sekme tamamlama da kullanılabilir:

```julia-repl
julia> x = 3 + 4im;

julia> x.[TAB][TAB]
im re

julia> import UUIDs

julia> UUIDs.uuid[TAB][TAB]
uuid1        uuid4         uuid5        uuid_version
```

Fonksiyonlardan çıkan çıktılar için alanlar da doldurulabilir:

```julia-repl
julia> split("","")[1].[TAB]
lastindex  offset  string
```

Fonksiyonlardan çıkan alanların tamamlanması tür çıkarımı kullanır ve yalnızca fonksiyon tür açısından kararlıysa alanları önerebilir.

Tamamlanma, giriş argümanlarıyla eşleşen mevcut yöntemlerin araştırılmasına yardımcı olabilir:

```julia-repl
julia> max([TAB] # All methods are displayed, not shown here due to size of the list

julia> max([1, 2], [TAB] # All methods where `Vector{Int}` matches as first argument
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281

julia> max([1, 2], max(1, 2), [TAB] # All methods matching the arguments.
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281
```

Anahtar kelimeler, aşağıda `limit` ve `keepempty` anahtar argümanlarının bulunduğu satırda olduğu gibi, önerilen yöntemlerde `;` sonrasında da görüntülenir:

```julia-repl
julia> split("1 1 1", [TAB]
split(str::AbstractString; limit, keepempty) in Base at strings/util.jl:302
split(str::T, splitter; limit, keepempty) where T<:AbstractString in Base at strings/util.jl:277
```

Yöntemlerin tamamlanması tür çıkarımını kullanır ve bu nedenle argümanların, argümanların fonksiyonlardan çıktısı olsa bile, eşleşip eşleşmediğini görebilir. Tamamlanmanın, eşleşmeyen yöntemleri kaldırabilmesi için fonksiyonun tür açısından kararlı olması gerekir.

Eğer belirli argüman türleriyle hangi yöntemlerin kullanılabileceğini merak ediyorsanız, fonksiyon adı olarak `?` kullanın. Bu, tek bir dize kabul eden InteractiveUtils'taki fonksiyonları aramanın bir örneğini gösterir:

```julia-repl
julia> InteractiveUtils.?("somefile")[TAB]
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
```

Bu, bir dize üzerinde çağrılabilen `InteractiveUtils` modülündeki listedeki yöntemlerdir. Varsayılan olarak, tüm argümanların `Any` olarak yazıldığı yöntemler hariç tutulur, ancak TAB yerine SHIFT-TAB tuşuna basarak bunları da görebilirsiniz:

```julia-repl
julia> InteractiveUtils.?("somefile")[SHIFT-TAB]
apropos(string) in REPL at REPL/src/docview.jl:796
clipboard(x) in InteractiveUtils at InteractiveUtils/src/clipboard.jl:64
code_llvm(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:221
code_native(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:243
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
edit(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:225
eval(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
include(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
less(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:274
report_bug(kind) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:391
separate_kwargs(args...; kwargs...) in InteractiveUtils at InteractiveUtils/src/macros.jl:7
```

Ayrıca `?("somefile")[TAB]` kullanabilir ve tüm modüllere göz atabilirsiniz, ancak yöntem listeleri uzun olabilir.

Parantezi kapatmayı atlayarak, ek argümanlar gerektirebilecek fonksiyonları dahil edebilirsiniz:

```julia-repl
julia> using Mmap

help?> Mmap.?("file",[TAB]
Mmap.Anonymous(name::String, readonly::Bool, create::Bool) in Mmap at Mmap/src/Mmap.jl:16
mmap(file::AbstractString) in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}) where T<:Array in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
```

## Customizing Colors

Julia ve REPL tarafından kullanılan renkler de özelleştirilebilir. Julia istemcisinin rengini değiştirmek için, ev dizininizde bulunan `~/.julia/config/startup.jl` dosyanıza aşağıdakine benzer bir şey ekleyebilirsiniz:

```julia
function customize_colors(repl)
    repl.prompt_color = Base.text_colors[:cyan]
end

atreplinit(customize_colors)
```

Mevcut renk anahtarları, REPL'nin yardım modunda `Base.text_colors` yazarak görülebilir. Ayrıca, 256 renk desteğine sahip terminaller için 0'dan 255'e kadar olan tam sayılar renk anahtarları olarak kullanılabilir.

Yardım ve kabuk istemleri ile girdi ve cevap metinlerinin renklerini, yukarıdaki `customize_colors` fonksiyonunda `repl`'in uygun alanlarını ayarlayarak değiştirebilirsiniz (sırasıyla, `help_color`, `shell_color`, `input_color` ve `answer_color`). Son iki alan için, `envcolors` alanının da false olarak ayarlandığından emin olun.

Ayrıca, kalın yazı biçimlendirmesini `Base.text_colors[:bold]` kullanarak bir renk olarak uygulamak da mümkündür. Örneğin, yanıtları kalın yazı tipiyle yazdırmak için aşağıdakini `~/.julia/config/startup.jl` olarak kullanabilirsiniz:

```julia
function customize_colors(repl)
    repl.envcolors = false
    repl.answer_color = Base.text_colors[:bold]
end

atreplinit(customize_colors)
```

Ayrıca, uyarı ve bilgilendirme mesajlarını oluşturmak için kullanılan rengi uygun ortam değişkenlerini ayarlayarak özelleştirebilirsiniz. Örneğin, hata, uyarı ve bilgilendirme mesajlarını sırasıyla magenta, sarı ve camgöbeği renginde oluşturmak için `~/.julia/config/startup.jl` dosyanıza aşağıdakileri ekleyebilirsiniz:

```julia
ENV["JULIA_ERROR_COLOR"] = :magenta
ENV["JULIA_WARN_COLOR"] = :yellow
ENV["JULIA_INFO_COLOR"] = :cyan
```

## Changing the contextual module which is active at the REPL

REPL'de ifadeler girildiğinde, varsayılan olarak `Main` modülünde değerlendirilir;

```julia-repl
julia> @__MODULE__
Main
```

Bu bağlamsal modülü `REPL.activate(m)` fonksiyonu aracılığıyla değiştirmek mümkündür; burada `m` bir `Modül`dür veya REPL'de modülü yazarak ve imleci modül adının üzerine getirip Alt-m tuş kombinasyonuna basarak (MacOS'ta Esc-m) değiştirebilirsiniz. Boş bir istemde tuş kombinasyonuna basmak, bağlamı daha önce aktif olan `Main` olmayan modül ile `Main` arasında değiştirir. Aktif modül, istemde gösterilir (eğer `Main` değilse):

```julia-repl
julia> using REPL

julia> REPL.activate(Base)

(Base) julia> @__MODULE__
Base

(Base) julia> using REPL # Need to load REPL into Base module to use it

(Base) julia> REPL.activate(Main)

julia>

julia> Core<Alt-m> # using the keybinding to change module

(Core) julia>

(Core) julia> <Alt-m> # going back to Main via keybinding

julia>

julia> <Alt-m> # going back to previously-active Core via keybinding

(Core) julia>
```

Opsiyonel bir modül argümanı alan fonksiyonlar genellikle REPL bağlamı modülüne varsayılan olarak ayarlanır. Örneğin, `varinfo()` çağrısı, mevcut aktif modülün değişkenlerini gösterecektir:

```julia-repl
julia> module CustomMod
           export var, f
           var = 1
           f(x) = x^2
       end;

julia> REPL.activate(CustomMod)

(Main.CustomMod) julia> varinfo()
  name         size summary
  ––––––––– ––––––– ––––––––––––––––––––––––––––––––––
  CustomMod         Module
  f         0 bytes f (generic function with 1 method)
  var       8 bytes Int64
```

## Numbered prompt

Bir IPython REPL ve Mathematica defteri ile benzer bir arayüze sahip olmak mümkündür; numaralı girdi istemleri ve çıktı ön ekleri ile. Bu, `REPL.numbered_prompt!()` çağrılarak yapılır. Bunu başlangıçta etkinleştirmek istiyorsanız, ekleyin

```julia
atreplinit() do repl
    @eval import REPL
    if !isdefined(repl, :interface)
        repl.interface = REPL.setup_interface(repl)
    end
    REPL.numbered_prompt!(repl)
end
```

`startup.jl` dosyanıza. Numaralı istemde `Out[n]` değişkeni (burada `n` bir tam sayı) daha önceki sonuçlara atıfta bulunmak için kullanılabilir:

```julia-repl
In [1]: 5 + 3
Out[1]: 8

In [2]: Out[1] + 5
Out[2]: 13

In [3]: Out
Out[3]: Dict{Int64, Any} with 2 entries:
  2 => 13
  1 => 8
```

!!! note
    `Out` değişkeninde önceki REPL değerlendirmelerinden gelen tüm çıktılar saklandığı için, birçok büyük bellek içi nesne (örneğin diziler) döndürüyorsanız dikkatli olmalısınız; çünkü bu nesnelere olan bir referans `Out` içinde kaldığı sürece çöp toplama işlemlerinden korunacaktır. `Out` içindeki nesnelere olan referansları kaldırmanız gerekiyorsa, sakladığı tüm geçmişi `empty!(Out)` ile temizleyebilir veya bireysel bir girişi `Out[n] = nothing` ile temizleyebilirsiniz.


## TerminalMenus

TerminalMenus, Julia REPL'in bir alt modülüdür ve terminalde küçük, düşük profilli etkileşimli menüler oluşturmayı sağlar.

### Examples

```julia
import REPL
using REPL.TerminalMenus

options = ["apple", "orange", "grape", "strawberry",
            "blueberry", "peach", "lemon", "lime"]

```

#### RadioMenu

RadioMenu, kullanıcının listeden bir seçenek seçmesine olanak tanır. `request` fonksiyonu etkileşimli menüyü görüntüler ve seçilen seçeneğin indeksini döndürür. Eğer bir kullanıcı 'q' tuşuna basarsa veya `ctrl-c` yaparsa, `request` `-1` döndürecektir.

```julia
# `pagesize` is the number of items to be displayed at a time.
#  The UI will scroll if the number of options is greater
#   than the `pagesize`
menu = RadioMenu(options, pagesize=4)

# `request` displays the menu and returns the index after the
#   user has selected a choice
choice = request("Choose your favorite fruit:", menu)

if choice != -1
    println("Your favorite fruit is ", options[choice], "!")
else
    println("Menu canceled.")
end

```

Çıktı:

```
Choose your favorite fruit:
^  grape
   strawberry
 > blueberry
v  peach
Your favorite fruit is blueberry!
```

#### MultiSelectMenu

MultiSelectMenu, kullanıcıların bir listeden birçok seçeneği seçmesine olanak tanır.

```julia
# here we use the default `pagesize` 10
menu = MultiSelectMenu(options)

# `request` returns a `Set` of selected indices
# if the menu us canceled (ctrl-c or q), return an empty set
choices = request("Select the fruits you like:", menu)

if length(choices) > 0
    println("You like the following fruits:")
    for i in choices
        println("  - ", options[i])
    end
else
    println("Menu canceled.")
end
```

Çıktı:

```
Select the fruits you like:
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
 > [X] orange
   [X] grape
   [ ] strawberry
   [ ] blueberry
   [X] peach
   [ ] lemon
   [ ] lime
You like the following fruits:
  - orange
  - grape
  - peach
```

### Customization / Configuration

#### ConfiguredMenu subtypes

Julia 1.6 ile birlikte, menüleri yapılandırmanın önerilen yolu yapıcı aracılığıyladır. Örneğin, varsayılan çoklu seçim menüsü

```
julia> menu = MultiSelectMenu(options, pagesize=5);

julia> request(menu) # ASCII is used by default
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
   [X] orange
   [ ] grape
 > [X] strawberry
v  [ ] blueberry
```

Unicode seçim ve navigasyon karakterleri ile yerine getirilebilir.

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode);

julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   ⬚ apple
   ✓ orange
   ⬚ grape
 → ✓ strawberry
↓  ⬚ blueberry
```

Daha ayrıntılı yapılandırma da mümkündür:

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode, checked="YEP!", unchecked="NOPE", cursor='⧐');

julia> request(menu)
julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   NOPE apple
   YEP! orange
   NOPE grape
 ⧐ YEP! strawberry
↓  NOPE blueberry
```

`charset` seçeneği dışında, `RadioMenu` için yapılandırılabilir seçenekler şunlardır:

  * `cursor::Char='>'|'→'`: imleç için kullanılacak karakter
  * `up_arrow::Char='^'|'↑'`: yukarı ok için kullanılacak karakter
  * `down_arrow::Char='v'|'↓'`: aşağı ok için kullanılacak karakter
  * `updown_arrow::Char='I'|'↕'`: yukarı/aşağı ok için bir satırlık sayfada kullanılacak karakter
  * `scroll_wrap::Bool=false`: menünün başında/sonunda isteğe bağlı olarak sarma yapar
  * `ctrl_c_interrupt::Bool=true`: Eğer `false` ise, ^C'de boş döner, eğer `true` ise ^C'de InterruptException() fırlatır.

`MultiSelectMenu` ekler:

  * `checked::String="[X]"|"✓"`: işaretli için kullanılacak dize
  * `unchecked::String="[ ]"|"⬚")`: işaretlenmemiş için kullanılacak dize

Kendi menü türlerinizi oluşturabilirsiniz. `TerminalMenus.ConfiguredMenu`'dan türetilen türler, menü seçeneklerini inşa zamanı sırasında yapılandırır.

#### Legacy interface

Julia 1.6'dan önce ve hala Julia 1.x boyunca desteklenen, menüleri `TerminalMenus.config()` çağrısı ile yapılandırmak da mümkündür.

## References

### REPL

```@docs
Base.atreplinit
```

### TerminalMenus

### Menus

```@docs
REPL.TerminalMenus.RadioMenu
REPL.TerminalMenus.MultiSelectMenu
```

#### Configuration

```@docs
REPL.TerminalMenus.Config
REPL.TerminalMenus.MultiSelectConfig
REPL.TerminalMenus.config
```

#### User interaction

```@docs
REPL.TerminalMenus.request
```

#### AbstractMenu extension interface

Herhangi bir `AbstractMenu` alt türü değiştirilebilir olmalı ve `pagesize::Int` ve `pageoffset::Int` alanlarını içermelidir. Her alt tür ayrıca aşağıdaki işlevleri de uygulamalıdır:

```@docs
REPL.TerminalMenus.pick
REPL.TerminalMenus.cancel
REPL.TerminalMenus.writeline
```

Ayrıca `options` veya `numoptions`'ı da uygulamalıdır:

```@docs
REPL.TerminalMenus.options
REPL.TerminalMenus.numoptions
```

Eğer alt türde `selected` adında bir alan yoksa, aynı zamanda uygulaması gerekir

```@docs
REPL.TerminalMenus.selected
```

Aşağıdakiler isteğe bağlıdır ancak ek özelleştirme sağlayabilir:

```@docs
REPL.TerminalMenus.header
REPL.TerminalMenus.keypress
```
