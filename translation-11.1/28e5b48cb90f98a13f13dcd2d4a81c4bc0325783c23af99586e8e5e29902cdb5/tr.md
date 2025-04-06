```
@styled_str -> AnnotatedString
```

Biçimlendirilmiş bir dize oluşturun. Dize içinde, `{<specs>:<content>}` yapıları `<content>`'e biçimlendirme uygular ve bu, virgülle ayrılmış `<specs>` spesifikasyonları listesini takip eder. Her bir spesifikasyon, bir yüz adı, bir satır içi yüz spesifikasyonu veya bir `key=value` çifti biçiminde olabilir. Değer, `,=:{}` karakterlerinden herhangi birini içeriyorsa `{...}` ile sarılmalıdır.

Dize interpolasyonu `$` ile, normal dizelerle aynı şekilde çalışır, ancak tırnak işaretleri kaçırılmalıdır. Yüzler, anahtarlar ve değerler de `$` ile interpolasyon yapılabilir.

# Örnek

```julia
styled"The {bold:{italic:quick} {(foreground=#cd853f):brown} fox} jumped over the {link={https://en.wikipedia.org/wiki/Laziness}:lazy} dog"
```

# Genişletilmiş yardım

Bu makro aşağıdaki EBNF grameri ile tanımlanabilir:

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
ws = { ' ' | '\t' | '\n' } ; (* boşluk *)

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

Yukarıdaki gramerde kodlanmamış bir ek şart, `plain`'in [`unescape_string`](@ref) için geçerli bir girdi olmasıdır ve `specialchar` korunmalıdır.

`inlineface` için yukarıdaki gramer basitleştirilmiştir, çünkü gerçek uygulama biraz daha karmaşıktır. Tam davranış aşağıda verilmiştir.

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
