```
@styled_str -> AnnotatedString
```

Konstruiere einen stilisierten String. Innerhalb des Strings wenden `{<specs>:<content>}`-Strukturen die Formatierung auf `<content>` an, gemäß der Liste von durch Kommas getrennten Spezifikationen `<specs>`. Jede Spezifikation kann entweder in Form eines Schriftgesichtsnamens, einer Inline-Schriftgesichtsspezifikation oder eines `key=value`-Paars vorliegen. Der Wert muss in `{...}` eingeschlossen werden, wenn er eines der Zeichen `,=:{}` enthält.

Die String-Interpolation mit `$` funktioniert auf die gleiche Weise wie bei regulären Strings, außer dass Anführungszeichen escaped werden müssen. Schriftgesichter, Schlüssel und Werte können ebenfalls mit `$` interpoliert werden.

# Beispiel

```julia
styled"The {bold:{italic:quick} {(foreground=#cd853f):brown} fox} jumped over the {link={https://en.wikipedia.org/wiki/Laziness}:lazy} dog"
```

# Erweiterte Hilfe

Dieses Makro kann durch die folgende EBNF-Grammatik beschrieben werden:

```ebnf
styledstring = { styled | interpolated | escaped | plain } ;

specialchar = '{' | '}' | '$' | '\"' ;
anychar = [\u0-\u1fffff] ;
plain = { anychar - specialchar } ;
escaped = '\\', specialchar ;

interpolated = '$', ? expr ? | '$(', ? expr ?, ')' ;

styled = '{', ws, annotations, ':', content, '}' ;
content = { interpolated | plain | escaped | styled } ;
annotations = annotation | annotations, ws, ',', ws, annotation ;
annotation = face | inlineface | keyvalue ;
ws = { ' ' | '\t' | '\n' } ; (* whitespace *)

face = facename | interpolated ;
facename = [A-Za-z0-9_]+ ;

inlineface = '(', ws, [ faceprop ], { ws, ',', faceprop }, ws, ')' ;
faceprop = [a-z]+, ws, '=', ws, ( [^,)]+ | interpolated) ;

keyvalue = key, ws, '=', ws, value ;
key = ( [^\0${}=,:], [^\0=,:]* ) | interpolated ;
value = simplevalue | curlybraced | interpolated ;
curlybraced = '{' { escaped | plain } '}' ;
simplevalue = [^${},:], [^,:]* ;
```

Eine zusätzliche Bestimmung, die nicht in der obigen Grammatik kodiert ist, ist, dass `plain` eine gültige Eingabe für [`unescape_string`](@ref) sein sollte, wobei `specialchar` beibehalten wird.

Die obige Grammatik für `inlineface` ist vereinfacht, da die tatsächliche Implementierung etwas ausgefeilter ist. Das vollständige Verhalten ist unten angegeben.

```ebnf
faceprop = ( 'face', ws, '=', ws, ( ? string ? | interpolated ) ) |
           ( 'height', ws, '=', ws, ( ? number ? | interpolated ) ) |
           ( 'weight', ws, '=', ws, ( symbol | interpolated ) ) |
           ( 'slant', ws, '=', ws, ( symbol | interpolated ) ) |
           ( ( 'foreground' | 'fg' | 'background' | 'bg' ),
               ws, '=', ws, ( simplecolor | interpolated ) ) |
           ( 'underline', ws, '=', ws, ( underline | interpolated ) ) |
           ( 'strikethrough', ws, '=', ws, ( bool | interpolated ) ) |
           ( 'inverse', ws, '=', ws, ( bool | interpolated ) ) |
           ( 'inherit', ws, '=', ws, ( inherit | interpolated ) ) ;

nothing = 'nothing' ;
bool = 'true' | 'false' ;
symbol = [^ ,)]+ ;
hexcolor = ('#' | '0x'), [0-9a-f]{6} ;
simplecolor = hexcolor | symbol | nothing ;

underline = nothing | bool | simplecolor | underlinestyled;
underlinestyled = '(', ws, ('' | nothing | simplecolor | interpolated), ws,
                  ',', ws, ( symbol | interpolated ), ws ')' ;

inherit = ( '[', inheritval, { ',', inheritval }, ']' ) | inheritval;
inheritval = ws, ':'?, symbol ;
```
