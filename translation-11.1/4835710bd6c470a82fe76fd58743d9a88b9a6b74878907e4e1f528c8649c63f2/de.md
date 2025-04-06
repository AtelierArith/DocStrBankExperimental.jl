# Unicode Input

Die folgende Tabelle listet Unicode-Zeichen auf, die über die Tab-Vervollständigung von LaTeX-ähnlichen Abkürzungen in der Julia REPL (und in verschiedenen anderen Bearbeitungsumgebungen) eingegeben werden können. Sie können auch Informationen darüber erhalten, wie man ein Symbol eingibt, indem Sie es in der REPL-Hilfe eingeben, d.h. indem Sie `?` eingeben und dann das Symbol in die REPL eingeben (z.B. durch Kopieren und Einfügen von irgendwo, wo Sie das Symbol gesehen haben).

!!! warning
    Diese Tabelle scheint möglicherweise fehlende Zeichen in der zweiten Spalte zu enthalten oder sogar Zeichen anzuzeigen, die inkonsistent mit den Zeichen sind, wie sie im Julia REPL gerendert werden. In diesen Fällen wird den Benutzern dringend geraten, ihre Schriftartenwahl in ihrem Browser und der REPL-Umgebung zu überprüfen, da es bekannte Probleme mit Glyphen in vielen Schriftarten gibt.


```@eval
#
# Generate a table containing all LaTeX and Emoji tab completions available in the REPL.
#
import REPL, Markdown
const NBSP = '\u00A0'

function tab_completions(symbols...)
    completions = Dict{String, Vector{String}}()
    for each in symbols, (k, v) in each
        completions[v] = push!(get!(completions, v, String[]), k)
    end
    return completions
end

function unicode_data()
    file = normpath(@__DIR__, "..", "..", "..", "..", "..", "doc", "UnicodeData.txt")
    names = Dict{UInt32, String}()
    open(file) do unidata
        for line in readlines(unidata)
            id, name, desc = split(line, ";")[[1, 2, 11]]
            codepoint = parse(UInt32, "0x$id")
            names[codepoint] = titlecase(lowercase(
                name == "" ? desc : desc == "" ? name : "$name / $desc"))
        end
    end
    return names
end

# Surround combining characters with no-break spaces (i.e '\u00A0'). Follows the same format
# for how unicode is displayed on the unicode.org website:
# https://util.unicode.org/UnicodeJsps/character.jsp?a=0300
function fix_combining_chars(char)
    cat = Base.Unicode.category_code(char)
    return cat == 6 || cat == 8 ? "$NBSP$char$NBSP" : "$char"
end

function table_entries(completions, unicode_dict)
    entries = Any[Any[
        ["Code point(s)"],
        ["Character(s)"],
        ["Tab completion sequence(s)"],
        ["Unicode name(s)"],
    ]]
    for (chars, inputs) in sort!(collect(completions), by = first)
        code_points, unicode_names, characters = String[], String[], String[]
        for char in chars
            push!(code_points, "U+$(uppercase(string(UInt32(char), base = 16, pad = 5)))")
            push!(unicode_names, get(unicode_dict, UInt32(char), "(No Unicode name)"))
            push!(characters, isempty(characters) ? fix_combining_chars(char) : "$char")
        end
        inputs_md = []
        for (i, input) in enumerate(inputs)
            i > 1 && push!(inputs_md, ", ")
            push!(inputs_md, Markdown.Code("", input))
        end
        push!(entries, [
            [join(code_points, " + ")],
            [join(characters)],
            inputs_md,
            [join(unicode_names, " + ")],
        ])
    end
    table = Markdown.Table(entries, [:l, :c, :l, :l])
    # We also need to wrap the Table in a Markdown.MD "document"
    return Markdown.MD([table])
end

table_entries(
    tab_completions(
        REPL.REPLCompletions.latex_symbols,
        REPL.REPLCompletions.emoji_symbols
    ),
    unicode_data()
)
```
