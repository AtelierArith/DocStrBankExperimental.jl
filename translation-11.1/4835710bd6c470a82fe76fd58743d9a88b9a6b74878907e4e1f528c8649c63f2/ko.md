# Unicode Input

다음 표는 Julia REPL(및 다양한 다른 편집 환경)에서 LaTeX와 유사한 약어의 탭 완성을 통해 입력할 수 있는 유니코드 문자를 나열합니다. 또한 REPL 도움말에 기호를 입력하여 기호를 입력하는 방법에 대한 정보를 얻을 수 있습니다. 즉, `?`를 입력한 다음 REPL에 기호를 입력하면 됩니다(예: 기호를 본 곳에서 복사-붙여넣기).

!!! warning
    이 표는 두 번째 열에 누락된 문자가 포함되어 있거나, Julia REPL에서 렌더링된 문자와 일치하지 않는 문자가 표시될 수 있습니다. 이러한 경우, 사용자는 브라우저와 REPL 환경에서 선택한 글꼴을 확인하는 것이 강력히 권장됩니다. 많은 글꼴에서 글리프와 관련된 알려진 문제가 있기 때문입니다.


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
