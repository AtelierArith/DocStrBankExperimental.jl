```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/REPL/docs/src/index.md"
```

# The Julia REPL

Julia kommt mit einer voll ausgestatteten interaktiven Befehlszeilen-REPL (read-eval-print loop), die in die `julia`-Ausführungsdatei integriert ist. Neben der schnellen und einfachen Auswertung von Julia-Anweisungen verfügt sie über eine durchsuchbare Historie, Tab-Vervollständigung, viele hilfreiche Tastenkombinationen sowie spezielle Hilfe- und Shell-Modi. Die REPL kann einfach gestartet werden, indem man `julia` ohne Argumente aufruft oder auf die ausführbare Datei doppelklickt:

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia>\n```")
```

Um die interaktive Sitzung zu beenden, geben Sie `^D` ein – die Steuerungstaste zusammen mit der `d`-Taste in einer leeren Zeile – oder geben Sie `exit()` gefolgt von der Rücktaste oder Eingabetaste ein. Der REPL begrüßt Sie mit einem Banner und einem `julia>`-Prompt.

## The different prompt modes

### The Julian mode

Der REPL hat fünf Hauptbetriebsmodi. Der erste und häufigste ist die Julian-Eingabeaufforderung. Es ist der Standardbetriebsmodus; jede neue Zeile beginnt zunächst mit `julia>`. Hier können Sie Julia-Ausdrücke eingeben. Das Drücken von Rücktaste oder Eingabetaste nach der Eingabe eines vollständigen Ausdrucks wertet den Eintrag aus und zeigt das Ergebnis des letzten Ausdrucks an.

```jldoctest
julia> string(1 + 2)
"3"
```

Es gibt eine Reihe nützlicher Funktionen, die interaktiver Arbeit eigen sind. Neben der Anzeige des Ergebnisses bindet die REPL das Ergebnis auch an die Variable `ans`. Ein nachgestelltes Semikolon am Ende der Zeile kann als Flag verwendet werden, um die Anzeige des Ergebnisses zu unterdrücken.

```jldoctest
julia> string(3 * 4);

julia> ans
"12"
```

Im Julia-Modus unterstützt die REPL etwas, das als *Prompt-Pasting* bezeichnet wird. Dies wird aktiviert, wenn Text, der mit `julia>` beginnt, in die REPL eingefügt wird. In diesem Fall werden nur Ausdrücke, die mit `julia>` beginnen (sowie die anderen REPL-Modus-Prompts: `shell>`, `help?>`, `pkg>`), geparst, während andere entfernt werden. Dies ermöglicht es, einen Textblock einzufügen, der aus einer REPL-Sitzung kopiert wurde, ohne die Prompts und Ausgaben entfernen zu müssen. Diese Funktion ist standardmäßig aktiviert, kann jedoch nach Belieben mit `REPL.enable_promptpaste(::Bool)` deaktiviert oder aktiviert werden. Wenn sie aktiviert ist, können Sie es ausprobieren, indem Sie den Codeblock über diesem Absatz direkt in die REPL einfügen. Diese Funktion funktioniert aufgrund ihrer Einschränkung beim Erkennen, wann ein Einfügen erfolgt, nicht im standardmäßigen Windows-Befehlszeilenprompt.

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

Um die Werte dieses Wörterbuchs beim Start automatisch zu definieren, kann man die [`atreplinit`](@ref)-Funktion in der `~/.julia/config/startup.jl`-Datei verwenden, zum Beispiel:

```julia
atreplinit() do repl
    repl.options.iocontext[:compact] = false
end
```

### Help mode

Wenn sich der Cursor am Anfang der Zeile befindet, kann die Eingabeaufforderung durch Eingabe von `?` in den Hilfemodus geändert werden. Julia wird versuchen, Hilfe oder Dokumentation für alles, was im Hilfemodus eingegeben wird, anzuzeigen:

```julia-repl
julia> ? # upon typing ?, the prompt changes (in place) to: help?>

help?> string
search: string String Cstring Cwstring RevString randstring bytestring SubString

  string(xs...)

  Create a string from any values using the print function.
```

Makros, Typen und Variablen können ebenfalls abgefragt werden:

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

Ein String- oder Regex-Literal durchsucht alle Docstrings mit [`apropos`](@ref):

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

Ein weiteres Merkmal des Hilfemodus ist die Möglichkeit, erweiterte Docstrings zuzugreifen. Sie können dies tun, indem Sie etwas wie `??Print` anstelle von `?Print` eingeben, was den Abschnitt `# Erweiterte Hilfe` aus der Dokumentation des Quellcodes anzeigt.

Der Hilfemodus kann verlassen werden, indem man die Rücktaste am Anfang der Zeile drückt.

### [Shell mode](@id man-shell-mode)

Genauso wie der Hilfemodus nützlich ist, um schnell auf die Dokumentation zuzugreifen, ist eine weitere häufige Aufgabe, die System-Shell zu verwenden, um Systembefehle auszuführen. Genauso wie `?` den Hilfemodus aktiviert, wenn es am Anfang der Zeile eingegeben wird, wird ein Semikolon (`;`) den Shell-Modus aktivieren. Und man kann ihn verlassen, indem man die Rücktaste am Anfang der Zeile drückt.

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> echo hello
hello
```

!!! note
    Für Windows-Benutzer gibt der Julia-Shell-Modus keine Windows-Shell-Befehle aus. Daher wird dies fehlschlagen:


```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> dir
ERROR: IOError: could not spawn `dir`: no such file or directory (ENOENT)
Stacktrace!
.......
```

Sie können jedoch auf `PowerShell` wie folgt zugreifen:

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.
PS C:\Users\elm>
```

... und zu `cmd.exe` so (siehe den Befehl `dir`):

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

Der Paketmanager-Modus akzeptiert spezialisierte Befehle zum Laden und Aktualisieren von Paketen. Er wird durch Drücken der `]`-Taste an der Julian REPL-Eingabeaufforderung betreten und durch Drücken von CTRL-C oder durch Drücken der Rücktaste am Anfang der Zeile verlassen. Die Eingabeaufforderung für diesen Modus ist `pkg>`. Er unterstützt seinen eigenen Hilfemodus, der durch Drücken von `?` am Anfang der Zeile der `pkg>`-Eingabeaufforderung betreten wird. Der Paketmanager-Modus ist im Pkg-Handbuch dokumentiert, das verfügbar ist unter [https://julialang.github.io/Pkg.jl/v1/](https://julialang.github.io/Pkg.jl/v1/).

### Search modes

In all of the above modes, the executed lines get saved to a history file, which can be searched.  To initiate an incremental search through the previous history, type `^R` – die Steuerungstaste zusammen mit der `r`-Taste. Die Eingabeaufforderung ändert sich zu ```(reverse-i-search)`':```, und während Sie tippen, wird die Suchanfrage in den Anführungszeichen angezeigt. Das aktuellste Ergebnis, das mit der Anfrage übereinstimmt, wird dynamisch rechts vom Doppelpunkt aktualisiert, während mehr eingegeben wird. Um ein älteres Ergebnis mit derselben Anfrage zu finden, tippen Sie einfach erneut `^R`.

Genauso wie `^R` eine Rückwärtssuche ist, ist `^S` eine Vorwärtssuche, mit der Eingabeaufforderung ```(i-search)`':```. Die beiden können zusammen verwendet werden, um durch die vorherigen oder nächsten Übereinstimmungen zu navigieren.

Alle ausgeführten Befehle in der Julia REPL werden in `~/.julia/logs/repl_history.jl` protokolliert, zusammen mit einem Zeitstempel, wann sie ausgeführt wurden, und dem aktuellen REPL-Modus, in dem Sie sich befanden. Der Suchmodus durchsucht diese Protokolldatei, um die Befehle zu finden, die Sie zuvor ausgeführt haben. Dies kann beim Start durch das Übergeben des Flags `--history-file=no` an Julia deaktiviert werden.

## Key bindings

Die Julia REPL nutzt die Tastenkombinationen hervorragend. Mehrere Steuerungstastenkombinationen wurden bereits oben eingeführt (`^D` zum Beenden, `^R` und `^S` zum Suchen), aber es gibt noch viele weitere. Neben der Steuerungstaste gibt es auch Meta-Tastenkombinationen. Diese variieren je nach Plattform, aber die meisten Terminals verwenden standardmäßig die Alt- oder Option-Taste, die zusammen mit einer Taste gedrückt wird, um die Meta-Taste zu senden (oder können so konfiguriert werden), oder drücken Esc und dann die Taste.

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

Julias REPL-Tastenkombinationen können vollständig an die Vorlieben des Benutzers angepasst werden, indem ein Wörterbuch an `REPL.setup_interface` übergeben wird. Die Schlüssel dieses Wörterbuchs können Zeichen oder Strings sein. Der Schlüssel `'*'` bezieht sich auf die Standardaktion. Steuerung plus Zeichen `x` Bindungen werden mit `"^x"` angezeigt. Meta plus `x` kann als `"\\M-x"` oder `"\ex"` geschrieben werden, und Steuerung plus `x` kann als `"\\C-x"` oder `"^x"` geschrieben werden. Die Werte der benutzerdefinierten Tastenkombinationen müssen `nothing` (was bedeutet, dass die Eingabe ignoriert werden soll) oder Funktionen sein, die die Signatur `(PromptState, AbstractREPL, Char)` akzeptieren. Die Funktion `REPL.setup_interface` muss aufgerufen werden, bevor die REPL initialisiert wird, indem die Operation mit [`atreplinit`](@ref) registriert wird. Um beispielsweise die Pfeiltasten nach oben und unten zu binden, um durch die Historie ohne Präfixsuche zu navigieren, könnte man den folgenden Code in `~/.julia/config/startup.jl` einfügen:

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

Benutzer sollten sich auf `LineEdit.jl` beziehen, um die verfügbaren Aktionen bei der Tasten Eingabe zu entdecken.

## Tab completion

Im Julian-, pkg- und Hilfsmodus des REPL kann man die ersten paar Zeichen einer Funktion oder eines Typs eingeben und dann die Tabulatortaste drücken, um eine Liste aller Übereinstimmungen zu erhalten:

```julia-repl
julia> x[TAB]
julia> xor
```

In einigen Fällen vervollständigt es nur einen Teil des Namens, bis zur nächsten Mehrdeutigkeit:

```julia-repl
julia> mapf[TAB]
julia> mapfold
```

Wenn Sie erneut die Tabulatortaste drücken, erhalten Sie die Liste der Dinge, die dies möglicherweise vervollständigen:

```julia-repl
julia> mapfold[TAB]
mapfoldl mapfoldr
```

Wenn am Ende einer Eingabezeile ein einzelnes vollständiges Tab-Vervollständigungsresultat verfügbar ist und 2 oder mehr Zeichen eingegeben wurden, wird ein Hinweis auf die Vervollständigung in einer helleren Farbe angezeigt. Dies kann deaktiviert werden über `Base.active_repl.options.hint_tab_completes = false`.

!!! compat "Julia 1.11"
    Tab-Vervollständigungshinweise wurden in Julia 1.11 hinzugefügt.


Wie andere Komponenten des REPL ist die Suche groß- und kleinschreibungsempfindlich:

```julia-repl
julia> stri[TAB]
stride     strides     string      strip

julia> Stri[TAB]
StridedArray    StridedMatrix    StridedVecOrMat  StridedVector    String
```

Die Tabulatortaste kann auch verwendet werden, um LaTeX-Mathematiksymbole durch ihre Unicode-Äquivalente zu ersetzen und eine Liste von LaTeX-Übereinstimmungen zu erhalten:

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

Eine vollständige Liste der Tab-Vervollständigungen finden Sie im Abschnitt [Unicode Input](@ref) des Handbuchs.

Die Vervollständigung von Pfaden funktioniert für Strings und Julias Shell-Modus:

```julia-repl
julia> path="/[TAB]"
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
shell> /[TAB]
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
```

Wörterbuchschlüssel können ebenfalls mit Tab vervollständigt werden:

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

Die Tab-Vervollständigung kann auch beim Ausfüllen von Feldern helfen:

```julia-repl
julia> x = 3 + 4im;

julia> x.[TAB][TAB]
im re

julia> import UUIDs

julia> UUIDs.uuid[TAB][TAB]
uuid1        uuid4         uuid5        uuid_version
```

Felder für die Ausgabe von Funktionen können ebenfalls ausgefüllt werden:

```julia-repl
julia> split("","")[1].[TAB]
lastindex  offset  string
```

Die Vervollständigung von Feldern für Ausgaben aus Funktionen verwendet Typinferenz, und sie kann Felder nur vorschlagen, wenn die Funktion typstabil ist.

Die Tab-Vervollständigung kann bei der Untersuchung der verfügbaren Methoden helfen, die den Eingabeargumenten entsprechen:

```julia-repl
julia> max([TAB] # All methods are displayed, not shown here due to size of the list

julia> max([1, 2], [TAB] # All methods where `Vector{Int}` matches as first argument
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281

julia> max([1, 2], max(1, 2), [TAB] # All methods matching the arguments.
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281
```

Schlüsselwörter werden auch in den vorgeschlagenen Methoden nach `;` angezeigt, siehe die folgende Zeile, in der `limit` und `keepempty` Schlüsselwortargumente sind:

```julia-repl
julia> split("1 1 1", [TAB]
split(str::AbstractString; limit, keepempty) in Base at strings/util.jl:302
split(str::T, splitter; limit, keepempty) where T<:AbstractString in Base at strings/util.jl:277
```

Die Vollständigkeit der Methoden verwendet Typinferenz und kann daher erkennen, ob die Argumente übereinstimmen, selbst wenn die Argumente aus Funktionen ausgegeben werden. Die Funktion muss typstabil sein, damit die Vollständigkeit nicht übereinstimmende Methoden entfernen kann.

Wenn Sie sich fragen, welche Methoden mit bestimmten Argumenttypen verwendet werden können, verwenden Sie `?` als Funktionsnamen. Dies zeigt ein Beispiel dafür, wie man in InteractiveUtils nach Funktionen sucht, die einen einzelnen String akzeptieren:

```julia-repl
julia> InteractiveUtils.?("somefile")[TAB]
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
```

Diese aufgelisteten Methoden im `InteractiveUtils`-Modul, die auf einen String aufgerufen werden können. Standardmäßig sind Methoden ausgeschlossen, bei denen alle Argumente als `Any` typisiert sind, aber Sie können diese ebenfalls sehen, indem Sie die SHIFT-TASTE gedrückt halten und dann die TAB-TASTE drücken:

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

Sie können auch `?("somefile")[TAB]` verwenden und in allen Modulen nachsehen, aber die Methodenlisten können lang sein.

Durch das Weglassen der schließenden Klammer können Sie Funktionen einbeziehen, die möglicherweise zusätzliche Argumente erfordern:

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

Die von Julia und dem REPL verwendeten Farben können ebenfalls angepasst werden. Um die Farbe der Julia-Eingabeaufforderung zu ändern, können Sie etwas Ähnliches wie das Folgende zu Ihrer `~/.julia/config/startup.jl`-Datei hinzufügen, die sich in Ihrem Home-Verzeichnis befinden sollte:

```julia
function customize_colors(repl)
    repl.prompt_color = Base.text_colors[:cyan]
end

atreplinit(customize_colors)
```

Die verfügbaren Farbtasten können gesehen werden, indem man `Base.text_colors` im Hilfemodus der REPL eingibt. Darüber hinaus können die Ganzzahlen von 0 bis 255 als Farbtasten für Terminals mit 256-Farben-Unterstützung verwendet werden.

Sie können auch die Farben für die Hilfe- und Shell-Eingabeaufforderungen sowie den Eingabe- und Antworttext ändern, indem Sie das entsprechende Feld von `repl` in der oben genannten Funktion `customize_colors` festlegen (jeweils `help_color`, `shell_color`, `input_color` und `answer_color`). Stellen Sie für die letzten beiden sicher, dass das Feld `envcolors` ebenfalls auf false gesetzt ist.

Es ist auch möglich, Fettdruckformatierung anzuwenden, indem `Base.text_colors[:bold]` als Farbe verwendet wird. Zum Beispiel kann man, um Antworten in fetter Schriftart auszugeben, Folgendes als `~/.julia/config/startup.jl` verwenden:

```julia
function customize_colors(repl)
    repl.envcolors = false
    repl.answer_color = Base.text_colors[:bold]
end

atreplinit(customize_colors)
```

Sie können auch die Farben anpassen, die zum Rendern von Warn- und Informationsnachrichten verwendet werden, indem Sie die entsprechenden Umgebungsvariablen festlegen. Um beispielsweise Fehler-, Warn- und Informationsnachrichten jeweils in Magenta, Gelb und Cyan darzustellen, können Sie Folgendes zu Ihrer `~/.julia/config/startup.jl`-Datei hinzufügen:

```julia
ENV["JULIA_ERROR_COLOR"] = :magenta
ENV["JULIA_WARN_COLOR"] = :yellow
ENV["JULIA_INFO_COLOR"] = :cyan
```

## Changing the contextual module which is active at the REPL

Beim Eingeben von Ausdrücken im REPL werden sie standardmäßig im `Main`-Modul ausgewertet;

```julia-repl
julia> @__MODULE__
Main
```

Es ist möglich, dieses kontextuelle Modul über die Funktion `REPL.activate(m)` zu ändern, wobei `m` ein `Modul` ist, oder indem man das Modul im REPL eingibt und die Tastenkombination Alt-m drückt, während der Cursor auf dem Modulnamen steht (Esc-m auf MacOS). Das Drücken der Tastenkombination an einer leeren Eingabeaufforderung wechselt den Kontext zwischen dem zuvor aktiven nicht-`Main`-Modul und `Main`. Das aktive Modul wird in der Eingabeaufforderung angezeigt (es sei denn, es ist `Main`):

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

Funktionen, die ein optionales Modulargument annehmen, verwenden oft standardmäßig das Modul des REPL-Kontexts. Als Beispiel zeigt der Aufruf von `varinfo()`, die Variablen des aktuell aktiven Moduls:

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

Es ist möglich, eine Schnittstelle zu erhalten, die der IPython REPL und dem Mathematica-Notebook mit nummerierten Eingabeaufforderungen und Ausgabepräfixen ähnelt. Dies wird erreicht, indem `REPL.numbered_prompt!()` aufgerufen wird. Wenn Sie dies beim Start aktivieren möchten, fügen Sie hinzu

```julia
atreplinit() do repl
    @eval import REPL
    if !isdefined(repl, :interface)
        repl.interface = REPL.setup_interface(repl)
    end
    REPL.numbered_prompt!(repl)
end
```

zu deiner `startup.jl`-Datei. In nummerierten Aufforderungen kann die Variable `Out[n]` (wobei `n` eine ganze Zahl ist) verwendet werden, um auf frühere Ergebnisse zu verweisen:

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
    Da alle Ausgaben aus vorherigen REPL-Auswertungen im `Out`-Variablen gespeichert sind, sollte man vorsichtig sein, wenn man viele große Objekte im Speicher wie Arrays zurückgibt, da sie so lange vor der Garbage Collection geschützt sind, wie eine Referenz auf sie in `Out` bleibt. Wenn Sie Referenzen auf Objekte in `Out` entfernen müssen, können Sie die gesamte Historie, die sie speichert, mit `empty!(Out)` löschen oder einen einzelnen Eintrag mit `Out[n] = nothing` löschen.


## TerminalMenus

TerminalMenus ist ein Submodul des Julia REPL und ermöglicht kleine, unauffällige interaktive Menüs im Terminal.

### Examples

```julia
import REPL
using REPL.TerminalMenus

options = ["apple", "orange", "grape", "strawberry",
            "blueberry", "peach", "lemon", "lime"]

```

#### RadioMenu

Das RadioMenu ermöglicht es dem Benutzer, eine Option aus der Liste auszuwählen. Die `request`-Funktion zeigt das interaktive Menü an und gibt den Index der ausgewählten Wahl zurück. Wenn ein Benutzer 'q' oder `ctrl-c` drückt, gibt `request` einen `-1` zurück.

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

Bitte fügen Sie den Markdown-Inhalt oder den Text ein, den Sie übersetzen möchten.

```
Choose your favorite fruit:
^  grape
   strawberry
 > blueberry
v  peach
Your favorite fruit is blueberry!
```

#### MultiSelectMenu

Das MultiSelectMenu ermöglicht es Benutzern, mehrere Auswahlmöglichkeiten aus einer Liste auszuwählen.

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

Bitte fügen Sie den Markdown-Inhalt oder den Text ein, den Sie übersetzen möchten.

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

Ab Julia 1.6 ist die empfohlene Methode zur Konfiguration von Menüs der Konstruktor. Zum Beispiel das Standard-Mehrfachauswahlmenü

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

kann stattdessen mit Unicode-Auswahl- und Navigationszeichen gerendert werden mit

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

Eine feinere Konfiguration ist ebenfalls möglich:

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

Neben der allgemeinen `charset`-Option sind die konfigurierbaren Optionen für `RadioMenu`:

  * `cursor::Char='>'|'→'`: Zeichen, das für den Cursor verwendet werden soll
  * `up_arrow::Char='^'|'↑'`: Zeichen, das für den Aufwärtspfeil verwendet wird
  * `down_arrow::Char='v'|'↓'`: Zeichen, das für den Abwärtspfeil verwendet wird
  * `updown_arrow::Char='I'|'↕'`: Zeichen, das für den Auf-/Abwärtspfeil auf einer einzeiligen Seite verwendet wird.
  * `scroll_wrap::Bool=false`: optional am Anfang/Ende eines Menüs umschließen
  * `ctrl_c_interrupt::Bool=true`: Wenn `false`, leere Rückgabe bei ^C, wenn `true`, wirf InterruptException() bei ^C

`MultiSelectMenu` fügt hinzu:

  * `checked::String="[X]"|"✓"`: Zeichenfolge, die für überprüft verwendet werden soll
  * `unchecked::String="[ ]"|"⬚")`: Zeichenfolge, die für nicht überprüft verwendet werden soll

Sie können neue Menütpyen Ihrer eigenen erstellen. Typen, die von `TerminalMenus.ConfiguredMenu` abgeleitet sind, konfigurieren die Menüoptionen zur Konstruktionszeit.

#### Legacy interface

Vor Julia 1.6 und weiterhin in Julia 1.x unterstützt, kann man auch Menüs konfigurieren, indem man `TerminalMenus.config()` aufruft.

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

Jeder Subtyp von `AbstractMenu` muss veränderlich sein und die Felder `pagesize::Int` und `pageoffset::Int` enthalten. Jeder Subtyp muss außerdem die folgenden Funktionen implementieren:

```@docs
REPL.TerminalMenus.pick
REPL.TerminalMenus.cancel
REPL.TerminalMenus.writeline
```

Es muss auch entweder `options` oder `numoptions` implementieren:

```@docs
REPL.TerminalMenus.options
REPL.TerminalMenus.numoptions
```

Wenn der Subtyp kein Feld mit dem Namen `selected` hat, muss er ebenfalls implementieren

```@docs
REPL.TerminalMenus.selected
```

Die folgenden sind optional, ermöglichen jedoch zusätzliche Anpassungen:

```@docs
REPL.TerminalMenus.header
REPL.TerminalMenus.keypress
```
