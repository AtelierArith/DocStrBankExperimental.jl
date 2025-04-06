```
;
```

`;` a un rôle similaire en Julia comme dans de nombreux langages de type C, et est utilisé pour délimiter la fin de l'instruction précédente.

`;` n'est pas nécessaire à la fin d'une ligne, mais peut être utilisé pour séparer des instructions sur une seule ligne ou pour joindre des instructions en une seule expression.

Ajouter `;` à la fin d'une ligne dans le REPL supprimera l'impression du résultat de cette expression.

Dans les déclarations de fonction, et optionnellement dans les appels, `;` sépare les arguments réguliers des mots-clés.

Dans les littéraux de tableau, les arguments séparés par des points-virgules ont leur contenu concaténé ensemble. Un séparateur composé d'un seul `;` concatène verticalement (c'est-à-dire le long de la première dimension), `;;` concatène horizontalement (deuxième dimension), `;;;` concatène le long de la troisième dimension, etc. Un tel séparateur peut également être utilisé en dernière position dans les crochets pour ajouter des dimensions supplémentaires de longueur 1.

Un `;` en première position à l'intérieur de parenthèses peut être utilisé pour construire un tuple nommé. La même syntaxe `(; ...)` sur le côté gauche d'une affectation permet de déstructurer des propriétés.

Dans le REPL standard, taper `;` sur une ligne vide passera en mode shell.

# Exemples

```jldoctest
julia> function foo()
           x = "Hello, "; x *= "World!"
           return x
       end
foo (generic function with 1 method)

julia> bar() = (x = "Hello, Mars!"; return x)
bar (generic function with 1 method)

julia> foo();

julia> bar()
"Hello, Mars!"

julia> function plot(x, y; style="solid", width=1, color="black")
           ###
       end

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [1; 3;; 2; 4;;; 10*A]
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 10  20
 30  40

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3

julia> nt = (; x=1) # sans le ; ou une virgule finale, cela assignerait à x
(x = 1,)

julia> key = :a; c = 3;

julia> nt2 = (; key => 1, b=2, c, nt.x)
(a = 1, b = 2, c = 3, x = 1)

julia> (; b, x) = nt2; # définir les variables b et x en utilisant la déstructuration de propriété

julia> b, x
(2, 1)

julia> ; # en tapant ;, l'invite change (sur place) en : shell>
shell> echo hello
hello
```
