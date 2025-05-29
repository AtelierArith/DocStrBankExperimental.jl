```
@transliterator(dict, name)
```

Create a custom transliterator using an input `dict` (`Dict` object) with its corresponding `name` as `String` object. This will automatically update the transliterator inside all  functions like `arabic`, `verses`, and `encode`.

# Examples

```julia-repl
julia> my_encoder = Dict(
    Symbol(Char(0x0621)) => Symbol('('),
    Symbol(Char(0x0622)) => Symbol('''),
    Symbol(Char(0x0623)) => Symbol('&'),
    Symbol(Char(0x0624)) => Symbol('>'),
    Symbol(Char(0x0625)) => Symbol('}'),
    Symbol(Char(0x0626)) => Symbol('<'),
    Symbol(Char(0x0627)) => Symbol('b'),
    Symbol(Char(0x0628)) => Symbol('A'),
    Symbol(Char(0x0629)) => Symbol('t'),
    Symbol(Char(0x062A)) => Symbol('p'),
    Symbol(Char(0x062B)) => Symbol('j'),
    Symbol(Char(0x062C)) => Symbol('v'),
    Symbol(Char(0x062D)) => Symbol('x'),
    Symbol(Char(0x062E)) => Symbol('H'),
    Symbol(Char(0x062F)) => Symbol('*'),
    Symbol(Char(0x0630)) => Symbol('d'),
    Symbol(Char(0x0631)) => Symbol('z'),
    Symbol(Char(0x0632)) => Symbol('r'),
    Symbol(Char(0x0633)) => Symbol('$'),
    Symbol(Char(0x0634)) => Symbol('s'),
    Symbol(Char(0x0635)) => Symbol('D'),
    Symbol(Char(0x0636)) => Symbol('S'),
    Symbol(Char(0x0637)) => Symbol('Z'),
    Symbol(Char(0x0638)) => Symbol('T'),
    Symbol(Char(0x0639)) => Symbol('g'),
    Symbol(Char(0x063A)) => Symbol('E'),
    Symbol(Char(0x0640)) => Symbol('f'),
    Symbol(Char(0x0641)) => Symbol('_'),
    Symbol(Char(0x0642)) => Symbol('k'),
    Symbol(Char(0x0643)) => Symbol('q'),
    Symbol(Char(0x0644)) => Symbol('m'),
    Symbol(Char(0x0645)) => Symbol('l'),
    Symbol(Char(0x0646)) => Symbol('h'),
    Symbol(Char(0x0647)) => Symbol('n'),
    Symbol(Char(0x0648)) => Symbol('Y'),
    Symbol(Char(0x0649)) => Symbol('w'),
    Symbol(Char(0x064A)) => Symbol('F'),
    Symbol(Char(0x064B)) => Symbol('y'),
    Symbol(Char(0x064C)) => Symbol('K'),
    Symbol(Char(0x064D)) => Symbol('N'),
    Symbol(Char(0x064E)) => Symbol('u'),
    Symbol(Char(0x064F)) => Symbol('a'),
    Symbol(Char(0x0650)) => Symbol('~'),
    Symbol(Char(0x0651)) => Symbol('i'),
    Symbol(Char(0x0652)) => Symbol('^'),
    Symbol(Char(0x0653)) => Symbol('o'),
    Symbol(Char(0x0654)) => Symbol('`'),
    Symbol(Char(0x0670)) => Symbol('#'),
    Symbol(Char(0x0671)) => Symbol(':'),
    Symbol(Char(0x06DC)) => Symbol('{'),
    Symbol(Char(0x06DF)) => Symbol('"'),
    Symbol(Char(0x06E0)) => Symbol('@'),
    Symbol(Char(0x06E2)) => Symbol(';'),
    Symbol(Char(0x06E3)) => Symbol('['),
    Symbol(Char(0x06E5)) => Symbol('.'),
    Symbol(Char(0x06E6)) => Symbol(','),
    Symbol(Char(0x06E8)) => Symbol('-'),
    Symbol(Char(0x06EA)) => Symbol('!'),
    Symbol(Char(0x06EB)) => Symbol('%'),
    Symbol(Char(0x06EC)) => Symbol('+'),
    Symbol(Char(0x06ED)) => Symbol(']')
);
julia> @transliterator my_encoder "MyEncoder"
julia> encode(ar_basmala)
"A~$^l~ :mmiun~ :mziux^lu#h~ :mziux~Fl~"
```
