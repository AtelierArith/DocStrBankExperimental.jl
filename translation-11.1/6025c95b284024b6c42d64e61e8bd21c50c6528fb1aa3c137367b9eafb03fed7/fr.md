# Noteworthy Differences from other Languages

## Noteworthy differences from MATLAB

Bien que les utilisateurs de MATLAB puissent trouver la syntaxe de Julia familière, Julia n'est pas un clone de MATLAB. Il existe d'importantes différences syntaxiques et fonctionnelles. Voici quelques différences notables qui peuvent dérouter les utilisateurs de Julia habitués à MATLAB :

  * Les tableaux Julia sont indexés avec des crochets, `A[i,j]`.
  * Les tableaux Julia ne sont pas copiés lorsqu'ils sont assignés à une autre variable. Après `A = B`, modifier les éléments de `B` modifiera également `A`. Pour éviter cela, utilisez `A = copy(B)`.
  * Les valeurs de Julia ne sont pas copiées lorsqu'elles sont passées à une fonction. Si une fonction modifie un tableau, les changements seront visibles dans l'appelant.
  * Julia ne fait pas automatiquement croître les tableaux dans une instruction d'affectation. Alors que dans MATLAB `a(4) = 3.2` peut créer le tableau `a = [0 0 0 3.2]` et `a(5) = 7` peut le faire croître en `a = [0 0 0 3.2 7]`, l'instruction correspondante en Julia `a[5] = 7` génère une erreur si la longueur de `a` est inférieure à 5 ou si cette instruction est la première utilisation de l'identifiant `a`. Julia a [`push!`](@ref) et [`append!`](@ref), qui font croître les `Vector`s beaucoup plus efficacement que `a(end+1) = val` de MATLAB.
  * L'unité imaginaire `sqrt(-1)` est représentée en Julia comme [`im`](@ref), et non `i` ou `j` comme dans MATLAB.
  * En Julia, les nombres littéraux sans point décimal (comme `42`) créent des entiers au lieu de nombres à virgule flottante. En conséquence, certaines opérations peuvent générer une erreur de domaine si elles s'attendent à un flottant ; par exemple, `julia> a = -1; 2^a` génère une erreur de domaine, car le résultat n'est pas un entier (voir [the FAQ entry on domain errors](@ref faq-domain-errors) pour plus de détails).
  * En Julia, plusieurs valeurs sont retournées et assignées sous forme de tuples, par exemple `(a, b) = (1, 2)` ou `a, b = 1, 2`. Le `nargout` de MATLAB, qui est souvent utilisé dans MATLAB pour effectuer un travail optionnel en fonction du nombre de valeurs retournées, n'existe pas en Julia. Au lieu de cela, les utilisateurs peuvent utiliser des arguments optionnels et des arguments nommés pour obtenir des capacités similaires.
  * Julia a de véritables tableaux unidimensionnels. Les vecteurs colonnes ont une taille de `N`, et non `Nx1`. Par exemple, [`rand(N)`](@ref) crée un tableau unidimensionnel.
  * En Julia, `[x,y,z]` construira toujours un tableau à 3 éléments contenant `x`, `y` et `z`.

      * Pour concaténer dans la première dimension ("verticale"), utilisez soit [`vcat(x,y,z)`](@ref) ou séparez avec des points-virgules (`[x; y; z]`).
      * Pour concaténer dans la deuxième dimension ("horizontale"), utilisez soit [`hcat(x,y,z)`](@ref) ou séparez avec des espaces (`[x y z]`).
      * Pour construire des matrices en blocs (en concaténant dans les deux premières dimensions), utilisez soit [`hvcat`](@ref) ou combinez des espaces et des points-virgules (`[a b; c d]`).
  * En Julia, `a:b` et `a:b:c` construisent des objets `AbstractRange`. Pour construire un vecteur complet comme dans MATLAB, utilisez [`collect(a:b)`](@ref). En général, il n'est pas nécessaire d'appeler `collect`. Un objet `AbstractRange` agira comme un tableau normal dans la plupart des cas, mais est plus efficace car il calcule ses valeurs de manière paresseuse. Ce modèle de création d'objets spécialisés au lieu de tableaux complets est utilisé fréquemment et se retrouve également dans des fonctions telles que [`range`](@ref), ou avec des itérateurs tels que `enumerate` et `zip`. Les objets spéciaux peuvent généralement être utilisés comme s'ils étaient des tableaux normaux.
  * Les fonctions en Julia renvoient des valeurs à partir de leur dernière expression ou du mot-clé `return` au lieu de lister les noms des variables à renvoyer dans la définition de la fonction (voir [The return Keyword](@ref) pour plus de détails).
  * Un script Julia peut contenir un nombre quelconque de fonctions, et toutes les définitions seront visibles de l'extérieur lorsque le fichier sera chargé. Les définitions de fonctions peuvent être chargées à partir de fichiers situés en dehors du répertoire de travail actuel.
  * En Julia, les réductions telles que [`sum`](@ref), [`prod`](@ref), et [`maximum`](@ref) sont effectuées sur chaque élément d'un tableau lorsqu'elles sont appelées avec un seul argument, comme dans `sum(A)`, même si `A` a plus d'une dimension.
  * En Julia, des parenthèses doivent être utilisées pour appeler une fonction sans arguments, comme dans [`rand()`](@ref).
  * Julia décourage l'utilisation de points-virgules pour terminer les instructions. Les résultats des instructions ne sont pas automatiquement imprimés (sauf à l'invite interactive), et les lignes de code n'ont pas besoin de se terminer par des points-virgules. [`println`](@ref) ou [`@printf`](@ref) peuvent être utilisés pour imprimer une sortie spécifique.
  * En Julia, si `A` et `B` sont des tableaux, les opérations de comparaison logique comme `A == B` ne renvoient pas un tableau de booléens. Utilisez plutôt `A .== B`, et de même pour les autres opérateurs booléens comme [`<`](@ref), [`>`](@ref).
  * En Julia, les opérateurs [`&`](@ref), [`|`](@ref), et [`⊻`](@ref xor) ([`xor`](@ref)) effectuent les opérations bit à bit équivalentes à `and`, `or`, et `xor` respectivement en MATLAB, et ont une priorité similaire aux opérateurs bit à bit de Python (contrairement à C). Ils peuvent fonctionner sur des scalaires ou de manière élémentaire à travers des tableaux et peuvent être utilisés pour combiner des tableaux logiques, mais notez la différence dans l'ordre des opérations : des parenthèses peuvent être nécessaires (par exemple, pour sélectionner les éléments de `A` égaux à 1 ou 2, utilisez `(A .== 1) .| (A .== 2)`).
  * En Julia, les éléments d'une collection peuvent être passés en tant qu'arguments à une fonction en utilisant l'opérateur splat `...`, comme dans `xs=[1,2]; f(xs...)`.
  * Le [`svd`](@ref) de Julia renvoie les valeurs singulières sous forme de vecteur au lieu d'une matrice diagonale dense.
  * En Julia, `...` n'est pas utilisé pour continuer les lignes de code. Au lieu de cela, les expressions incomplètes se poursuivent automatiquement sur la ligne suivante.
  * Dans Julia et MATLAB, la variable `ans` est définie sur la valeur de la dernière expression émise dans une session interactive. Dans Julia, contrairement à MATLAB, `ans` n'est pas défini lorsque le code Julia est exécuté en mode non interactif.
  * Les `struct`s de Julia ne prennent pas en charge l'ajout dynamique de champs à l'exécution, contrairement aux `class`es de MATLAB. Utilisez plutôt un [`Dict`](@ref). Le Dict en Julia n'est pas ordonné.
  * En Julia, chaque module a son propre scope/namespace global, tandis qu'en MATLAB, il n'y a qu'un seul scope global.
  * En MATLAB, une manière idiomatique de supprimer des valeurs indésirables est d'utiliser l'indexation logique, comme dans l'expression `x(x>3)` ou dans l'instruction `x(x>3) = []` pour modifier `x` sur place. En revanche, Julia fournit les fonctions d'ordre supérieur [`filter`](@ref) et [`filter!`](@ref), permettant aux utilisateurs d'écrire `filter(z->z>3, x)` et `filter!(z->z>3, x)` comme alternatives aux translittérations correspondantes `x[x.>3]` et `x = x[x.>3]`. L'utilisation de `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` réduit l'utilisation de tableaux temporaires.
  * L'analogue de l'extraction (ou "déréférencement") de tous les éléments d'un tableau de cellules, par exemple dans `vertcat(A{:})` en MATLAB, s'écrit en utilisant l'opérateur splat en Julia, par exemple comme `vcat(A...)`.
  * En Julia, la fonction `adjoint` effectue une transposition conjuguée ; dans MATLAB, `adjoint` fournit l'"adjugé" ou adjoint classique, qui est la transposition de la matrice des cofacteurs.
  * En Julia, a^b^c est évalué comme a^(b^c) tandis qu'en MATLAB, c'est (a^b)^c.

## Noteworthy differences from R

Un des objectifs de Julia est de fournir un langage efficace pour l'analyse de données et la programmation statistique. Pour les utilisateurs venant de R, voici quelques différences notables :

  * Les guillemets simples de Julia englobent des caractères, pas des chaînes.
  * Julia peut créer des sous-chaînes en indexant dans des chaînes. En R, les chaînes doivent être converties en vecteurs de caractères avant de créer des sous-chaînes.
  * En Julia, comme en Python mais contrairement à R, les chaînes de caractères peuvent être créées avec des triples guillemets `""" ... """`. Cette syntaxe est pratique pour construire des chaînes qui contiennent des sauts de ligne.
  * En Julia, les varargs sont spécifiés en utilisant l'opérateur splat `...`, qui suit toujours le nom d'une variable spécifique, contrairement à R, où `...` peut apparaître isolément.
  * En Julia, le module est `mod(a, b)`, pas `a %% b`. `%` en Julia est l'opérateur de reste.
  * Julia construit des vecteurs en utilisant des crochets. Le `[1, 2, 3]` de Julia est l'équivalent du `c(1, 2, 3)` de R.
  * En Julia, toutes les structures de données ne prennent pas en charge l'indexation logique. De plus, l'indexation logique en Julia n'est prise en charge qu'avec des vecteurs de longueur égale à l'objet indexé. Par exemple :

      * En R, `c(1, 2, 3, 4)[c(TRUE, FALSE)]` est équivalent à `c(1, 3)`.
      * En R, `c(1, 2, 3, 4)[c(TRUE, FALSE, TRUE, FALSE)]` est équivalent à `c(1, 3)`.
      * En Julia, `[1, 2, 3, 4][[true, false]]` lance une [`BoundsError`](@ref).
      * En Julia, `[1, 2, 3, 4][[true, false, true, false]]` produit `[1, 3]`.
  * Comme beaucoup de langages, Julia ne permet pas toujours les opérations sur des vecteurs de longueurs différentes, contrairement à R où les vecteurs n'ont besoin de partager qu'une plage d'index commune. Par exemple, `c(1, 2, 3, 4) + c(1, 2)` est valide en R mais l'équivalent `[1, 2, 3, 4] + [1, 2]` générera une erreur en Julia.
  * Julia permet une virgule finale optionnelle lorsque cette virgule ne change pas le sens du code. Cela peut causer de la confusion parmi les utilisateurs de R lors de l'indexation dans des tableaux. Par exemple, `x[1,]` en R renverrait la première ligne d'une matrice ; en Julia, cependant, la virgule est ignorée, donc `x[1,] == x[1]`, et renverra le premier élément. Pour extraire une ligne, assurez-vous d'utiliser `:`, comme dans `x[1,:]`.
  * Le [`map`](@ref) de Julia prend d'abord la fonction, puis ses arguments, contrairement à `lapply(<structure>, function, ...)` en R. De même, l'équivalent de Julia de `apply(X, MARGIN, FUN, ...)` en R est [`mapslices`](@ref) où la fonction est le premier argument.
  * L'application multivariée en R, par exemple `mapply(choose, 11:13, 1:3)`, peut être écrite comme `broadcast(binomial, 11:13, 1:3)` en Julia. Équivalemment, Julia propose une syntaxe de point plus courte pour vectoriser les fonctions `binomial.(11:13, 1:3)`.
  * Julia utilise `end` pour indiquer la fin des blocs conditionnels, comme `if`, des blocs de boucle, comme `while`/ `for`, et des fonctions. Au lieu de la syntaxe d'une ligne `if ( cond ) statement`, Julia permet des instructions de la forme `if cond; statement; end`, `cond && statement` et `!cond || statement`. Les instructions d'assignation dans les deux dernières syntaxes doivent être explicitement enveloppées entre parenthèses, par exemple `cond && (x = value)`.
  * En Julia, `<-`, `<<-` et `->` ne sont pas des opérateurs d'assignation.
  * Le `->` de Julia crée une fonction anonyme.
  * L'opérateur [`*`](@ref) de Julia peut effectuer une multiplication de matrices, contrairement à R. Si `A` et `B` sont des matrices, alors `A * B` désigne une multiplication de matrices en Julia, équivalente à `A %*% B` en R. Dans R, cette même notation effectuerait un produit élément par élément (Hadamard). Pour obtenir l'opération de multiplication élément par élément, vous devez écrire `A .* B` en Julia.
  * Julia effectue la transposition de matrices en utilisant la fonction `transpose` et la transposition conjuguée en utilisant l'opérateur `'` ou la fonction `adjoint`. La fonction `transpose(A)` de Julia est donc équivalente à `t(A)` de R. De plus, une transposition non récursive en Julia est fournie par la fonction `permutedims`.
  * Julia ne nécessite pas de parenthèses lors de l'écriture des instructions `if` ou des boucles `for`/`while` : utilisez `for i in [1, 2, 3]` au lieu de `for (i in c(1, 2, 3))` et `if i == 1` au lieu de `if (i == 1)`.
  * Julia ne traite pas les nombres `0` et `1` comme des booléens. Vous ne pouvez pas écrire `if (1)` en Julia, car les instructions `if` n'acceptent que des booléens. Au lieu de cela, vous pouvez écrire `if true`, `if Bool(1)`, ou `if 1==1`.
  * Julia ne fournit pas `nrow` et `ncol`. Utilisez plutôt `size(M, 1)` pour `nrow(M)` et `size(M, 2)` pour `ncol(M)`.
  * Julia fait attention à distinguer les scalaires, les vecteurs et les matrices. En R, `1` et `c(1)` sont identiques. En Julia, ils ne peuvent pas être utilisés de manière interchangeable.
  * Le [`diag`](@ref) et le [`diagm`](@ref) de Julia ne ressemblent pas à ceux de R.
  * Julia ne peut pas assigner aux résultats des appels de fonction sur le côté gauche d'une opération d'assignation : vous ne pouvez pas écrire `diag(M) = fill(1, n)`.
  * Julia décourage de peupler l'espace de noms principal avec des fonctions. La plupart des fonctionnalités statistiques pour Julia se trouvent dans [packages](https://pkg.julialang.org/) sous [JuliaStats organization](https://github.com/JuliaStats). Par exemple :

      * Les fonctions relatives aux distributions de probabilité sont fournies par le [Distributions package](https://github.com/JuliaStats/Distributions.jl).
      * Le [DataFrames package](https://github.com/JuliaData/DataFrames.jl) fournit des cadres de données.
      * Les modèles linéaires généralisés sont fournis par le [GLM package](https://github.com/JuliaStats/GLM.jl).
  * Julia fournit des tuples et des tables de hachage réelles, mais pas de listes de style R. Lors du retour de plusieurs éléments, vous devez généralement utiliser un tuple ou un tuple nommé : au lieu de `list(a = 1, b = 2)`, utilisez `(1, 2)` ou `(a=1, b=2)`.
  * Julia encourage les utilisateurs à écrire leurs propres types, qui sont plus faciles à utiliser que les objets S3 ou S4 dans R. Le système de dispatch multiple de Julia signifie que `table(x::TypeA)` et `table(x::TypeB)` agissent comme `table.TypeA(x)` et `table.TypeB(x)` dans R.
  * En Julia, les valeurs ne sont pas copiées lorsqu'elles sont assignées ou passées à une fonction. Si une fonction modifie un tableau, les changements seront visibles dans l'appelant. C'est très différent de R et permet aux nouvelles fonctions d'opérer sur de grandes structures de données de manière beaucoup plus efficace.
  * En Julia, les vecteurs et les matrices sont concaténés en utilisant [`hcat`](@ref), [`vcat`](@ref) et [`hvcat`](@ref), et non `c`, `rbind` et `cbind` comme en R.
  * En Julia, une plage comme `a:b` n'est pas une abréviation pour un vecteur comme en R, mais est un objet `AbstractRange` spécialisé qui est utilisé pour l'itération. Pour convertir une plage en vecteur, utilisez [`collect(a:b)`](@ref).
  * L'opérateur `:` a une priorité différente dans R et Julia. En particulier, dans Julia, les opérateurs arithmétiques ont une priorité plus élevée que l'opérateur `:`, tandis que l'inverse est vrai dans R. Par exemple, `1:n-1` dans Julia est équivalent à `1:(n-1)` dans R.
  * Le [`max`](@ref) et le [`min`](@ref) de Julia sont l'équivalent de `pmax` et `pmin` respectivement en R, mais les deux arguments doivent avoir les mêmes dimensions. Alors que le [`maximum`](@ref) et le [`minimum`](@ref) remplacent `max` et `min` en R, il existe des différences importantes.
  * Le [`sum`](@ref), [`prod`](@ref), [`maximum`](@ref), et [`minimum`](@ref) de Julia sont différents de leurs homologues en R. Ils acceptent tous un argument clé optionnel `dims`, qui indique les dimensions sur lesquelles l'opération est effectuée. Par exemple, soit `A = [1 2; 3 4]` en Julia et `B <- rbind(c(1,2),c(3,4))` étant la même matrice en R. Alors `sum(A)` donne le même résultat que `sum(B)`, mais `sum(A, dims=1)` est un vecteur ligne contenant la somme de chaque colonne et `sum(A, dims=2)` est un vecteur colonne contenant la somme de chaque ligne. Cela contraste avec le comportement de R, où des fonctions séparées `colSums(B)` et `rowSums(B)` fournissent ces fonctionnalités. Si l'argument clé `dims` est un vecteur, alors il spécifie toutes les dimensions sur lesquelles la somme est effectuée, tout en conservant les dimensions du tableau sommé, par exemple `sum(A, dims=(1,2)) == hcat(10)`. Il convient de noter qu'il n'y a pas de vérification d'erreur concernant le deuxième argument.
  * Julia a plusieurs fonctions qui peuvent muter leurs arguments. Par exemple, elle a à la fois [`sort`](@ref) et [`sort!`](@ref).
  * En R, la performance nécessite la vectorisation. En Julia, presque le contraire est vrai : le code le plus performant est souvent obtenu en utilisant des boucles dévectorisées.
  * Julia est évaluée de manière anticipée et ne prend pas en charge l'évaluation paresseuse de style R. Pour la plupart des utilisateurs, cela signifie qu'il y a très peu d'expressions non citées ou de noms de colonnes.
  * Julia ne prend pas en charge le type `NULL`. L'équivalent le plus proche est [`nothing`](@ref), mais il se comporte comme une valeur scalaire plutôt que comme une liste. Utilisez `x === nothing` au lieu de `is.null(x)`.
  * En Julia, les valeurs manquantes sont représentées par l'objet [`missing`](@ref) plutôt que par `NA`. Utilisez [`ismissing(x)`](@ref) (ou `ismissing.(x)` pour une opération élément par élément sur des vecteurs) au lieu de `is.na(x)`. La fonction [`skipmissing`](@ref) est généralement utilisée au lieu de `na.rm=TRUE` (bien que dans certains cas particuliers, des fonctions prennent un argument `skipmissing`).
  * Julia n'a pas l'équivalent de `assign` ou `get` de R.
  * En Julia, `return` ne nécessite pas de parenthèses.
  * En R, une manière idiomatique de supprimer des valeurs indésirables est d'utiliser l'indexation logique, comme dans l'expression `x[x>3]` ou dans l'instruction `x = x[x>3]` pour modifier `x` sur place. En revanche, Julia fournit les fonctions d'ordre supérieur [`filter`](@ref) et [`filter!`](@ref), permettant aux utilisateurs d'écrire `filter(z->z>3, x)` et `filter!(z->z>3, x)` comme alternatives aux translittérations correspondantes `x[x.>3]` et `x = x[x.>3]`. L'utilisation de `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` réduit l'utilisation de tableaux temporaires.

## Noteworthy differences from Python

  * Les blocs `for`, `if`, `while`, etc. de Julia se terminent par le mot-clé `end`. Le niveau d'indentation n'est pas significatif comme c'est le cas en Python. Contrairement à Python, Julia n'a pas de mot-clé `pass`.
  * Les chaînes de caractères sont désignées par des guillemets doubles (`"texte"`) en Julia (avec trois guillemets doubles pour les chaînes multi-lignes), tandis qu'en Python, elles peuvent être désignées soit par des guillemets simples (`'texte'`), soit par des guillemets doubles (`"texte"`). Les guillemets simples sont utilisés pour les caractères en Julia (`'c'`).
  * La concaténation de chaînes se fait avec `*` en Julia, et non `+` comme en Python. De manière analogue, la répétition de chaînes se fait avec `^`, et non `*`. La concaténation implicite de littéraux de chaînes comme en Python (par exemple, `'ab' 'cd' == 'abcd'`) n'est pas faite en Julia.
  * Les listes Python—flexibles mais lentes—correspondent au type `Vector{Any}` de Julia ou plus généralement à `Vector{T}` où `T` est un type d'élément non concret. Les tableaux "rapides" comme les tableaux NumPy qui stockent les éléments en place (c'est-à-dire, `dtype` est `np.float64`, `[('f1', np.uint64), ('f2', np.int32)]`, etc.) peuvent être représentés par `Array{T}` où `T` est un type d'élément concret et immuable. Cela inclut des types intégrés comme `Float64`, `Int32`, `Int64` mais aussi des types plus complexes comme `Tuple{UInt64,Float64}` et de nombreux types définis par l'utilisateur également.
  * En Julia, l'indexation des tableaux, des chaînes, etc. est basée sur 1 et non sur 0.
  * L'indexation des tranches de Julia inclut le dernier élément, contrairement à Python. `a[2:3]` en Julia est `a[1:3]` en Python.
  * Contrairement à Python, Julia permet [AbstractArrays with arbitrary indexes](https://julialang.org/blog/2017/04/offset-arrays/). L'interprétation spéciale de l'indexation négative en Python, `a[-1]` et `a[-2]`, doit être écrite `a[end]` et `a[end-1]` en Julia.
  * Julia nécessite `end` pour indexer jusqu'au dernier élément. `x[1:]` en Python est équivalent à `x[2:end]` en Julia.
  * En Julia, `:` avant tout objet crée un [`Symbol`](@ref) ou *met en guillemets* une expression ; donc, `x[:5]` est identique à `x[5]`. Si vous souhaitez obtenir les premiers `n` éléments d'un tableau, utilisez l'indexation par plage.
  * L'indexation de plage de Julia a le format `x[start:step:stop]`, tandis que le format de Python est `x[start:(stop+1):step]`. Ainsi, `x[0:10:2]` en Python est équivalent à `x[1:2:10]` en Julia. De même, `x[::-1]` en Python, qui fait référence au tableau inversé, est équivalent à `x[end:-1:1]` en Julia.
  * En Julia, les plages peuvent être construites indépendamment sous la forme `début:pas:fin`, la même syntaxe utilisée pour l'indexation des tableaux. La fonction `range` est également supportée.
  * En Julia, indexer une matrice avec des tableaux comme `X[[1,2], [1,3]]` fait référence à une sous-matrice qui contient les intersections des première et deuxième lignes avec les première et troisième colonnes. En Python, `X[[1,2], [1,3]]` fait référence à un vecteur qui contient les valeurs des cellules `[1,1]` et `[2,3]` dans la matrice. `X[[1,2], [1,3]]` en Julia est équivalent à `X[np.ix_([0,1],[0,2])]` en Python. `X[[0,1], [0,2]]` en Python est équivalent à `X[[CartesianIndex(1,1), CartesianIndex(2,3)]]` en Julia.
  * Julia n'a pas de syntaxe de continuation de ligne : si, à la fin d'une ligne, l'entrée jusqu'à présent est une expression complète, elle est considérée comme terminée ; sinon, l'entrée continue. Une façon de forcer une expression à continuer est de l'envelopper dans des parenthèses.
  * Julia arrays are column-major (Fortran-ordered) whereas NumPy arrays are row-major (C-ordered) by default. To get optimal performance when looping over arrays, the order of the loops should be reversed in Julia relative to NumPy (see [relevant section of Performance Tips](@ref man-performance-column-major)).
  * Les opérateurs de mise à jour de Julia (par exemple `+=`, `-=`, ...) ne sont *pas en place* alors que ceux de NumPy le sont. Cela signifie que `A = [1, 1]; B = A; B += [3, 3]` ne change pas les valeurs dans `A`, mais réaffecte plutôt le nom `B` au résultat du côté droit `B = B + 3`, qui est un nouveau tableau. Pour une opération en place, utilisez `B .+= 3` (voir aussi [dot operators](@ref man-dot-operators)), des boucles explicites ou `InplaceOps.jl`.
  * Julia évalue les valeurs par défaut des arguments de fonction chaque fois que la méthode est invoquée, contrairement à Python où les valeurs par défaut sont évaluées une seule fois lors de la définition de la fonction. Par exemple, la fonction `f(x=rand()) = x` renvoie un nouveau nombre aléatoire chaque fois qu'elle est invoquée sans argument. D'autre part, la fonction `g(x=[1,2]) = push!(x,3)` renvoie `[1,2,3]` chaque fois qu'elle est appelée avec `g()`.
  * En Julia, les arguments de mot-clé doivent être passés en utilisant des mots-clés, contrairement à Python où il est généralement possible de les passer par position. Tenter de passer un argument de mot-clé par position modifie la signature de la méthode, entraînant une `MethodError` ou l'appel de la mauvaise méthode.
  * En Julia, `%` est l'opérateur de reste, tandis qu'en Python, c'est le module.
  * En Julia, le type `Int` couramment utilisé correspond au type entier machine (`Int32` ou `Int64`), contrairement à Python, où `int` est un entier de longueur arbitraire. Cela signifie qu'en Julia, le type `Int` débordera, de sorte que `2^64 == 0`. Si vous avez besoin de valeurs plus grandes, utilisez un autre type approprié, tel que `Int128`, [`BigInt`](@ref) ou un type à virgule flottante comme `Float64`.
  * L'unité imaginaire `sqrt(-1)` est représentée en Julia par `im`, et non par `j` comme en Python.
  * En Julia, l'opérateur d'exponentiation est `^`, pas `**` comme en Python.
  * Julia utilise `nothing` de type `Nothing` pour représenter une valeur nulle, tandis que Python utilise `None` de type `NoneType`.
  * En Julia, les opérateurs standard sur un type de matrice sont des opérations matricielles, tandis qu'en Python, les opérateurs standard sont des opérations élément par élément. Lorsque `A` et `B` sont des matrices, `A * B` en Julia effectue une multiplication matricielle, et non une multiplication élément par élément comme en Python. `A * B` en Julia est équivalent à `A @ B` en Python, tandis que `A * B` en Python est équivalent à `A .* B` en Julia.
  * L'opérateur adjoint `'` en Julia renvoie un adjoint d'un vecteur (une représentation paresseuse d'un vecteur ligne), tandis que l'opérateur de transposition `.T` sur un vecteur en Python renvoie le vecteur d'origine (non-op).
  * En Julia, une fonction peut contenir plusieurs implémentations concrètes (appelées *méthodes*), qui sont sélectionnées via le dispatch multiple en fonction des types de tous les arguments de l'appel, contrairement aux fonctions en Python, qui ont une seule implémentation et pas de polymorphisme (contrairement aux appels de méthode en Python qui utilisent une syntaxe différente et permettent le dispatch sur le récepteur de la méthode).
  * Il n'y a pas de classes en Julia. À la place, il y a des structures (mutables ou immuables), contenant des données mais pas de méthodes.
  * Appeler une méthode d'une instance de classe en Python (`x = MyClass(*args); x.f(y)`) correspond à un appel de fonction en Julia, par exemple `x = MyType(args...); f(x, y)`. En général, le dispatch multiple est plus flexible et puissant que le système de classes de Python.
  * Les structures Julia peuvent avoir exactement un supertype abstrait, tandis que les classes Python peuvent hériter d'une ou plusieurs superclasses (abstraites ou concrètes).
  * La structure logique du programme Julia (Packages et Modules) est indépendante de la structure des fichiers, tandis que la structure du code Python est définie par des répertoires (Packages) et des fichiers (Modules).
  * En Julia, il est idiomatique de diviser le texte de grands modules en plusieurs fichiers, sans introduire un nouveau module par fichier. Le code est réassemblé à l'intérieur d'un seul module dans un fichier principal via `include`. Bien que l'équivalent en Python (`exec`) ne soit pas typique pour cet usage (il écrasera silencieusement les définitions précédentes), les programmes Julia sont définis comme une unité au niveau du `module` avec `using` ou `import`, qui ne seront exécutés qu'une seule fois lorsqu'ils seront d'abord nécessaires – comme `include` en Python. Au sein de ces modules, les fichiers individuels qui composent ce module sont chargés avec `include` en les listant une fois dans l'ordre souhaité.
  * L'opérateur ternaire `x > 0 ? 1 : -1` en Julia correspond à une expression conditionnelle en Python `1 if x > 0 else -1`.
  * En Julia, le symbole `@` fait référence à un macro, tandis qu'en Python, il fait référence à un décorateur.
  * La gestion des exceptions en Julia se fait en utilisant `try` — `catch` — `finally`, au lieu de `try` — `except` — `finally`. Contrairement à Python, il n'est pas recommandé d'utiliser la gestion des exceptions comme partie intégrante du flux de travail normal en Julia (comparé à Python, Julia est plus rapide pour le flux de contrôle ordinaire mais plus lent pour la capture d'exceptions).
  * En Julia, les boucles sont rapides, il n'est pas nécessaire d'écrire du code "vectorisé" pour des raisons de performance.
  * Faites attention aux variables globales non constantes en Julia, surtout dans des boucles serrées. Étant donné que vous pouvez écrire du code proche du métal en Julia (contrairement à Python), l'effet des variables globales peut être drastique (voir [Performance Tips](@ref man-performance-tips)).
  * En Julia, l'arrondi et la troncature sont explicites. L'utilisation de `int(3.7)` en Python devrait être `floor(Int, 3.7)` ou `Int(floor(3.7))` et se distingue de `round(Int, 3.7)`. `floor(x)` et `round(x)` à eux seuls renvoient une valeur entière du même type que `x` plutôt que de toujours renvoyer `Int`.
  * En Julia, l'analyse est explicite. Le `float("3.7")` de Python serait `parse(Float64, "3.7")` en Julia.
  * En Python, la majorité des valeurs peuvent être utilisées dans des contextes logiques (par exemple, `if "a":` signifie que le bloc suivant est exécuté, et `if "":` signifie qu'il ne l'est pas). En Julia, vous devez effectuer une conversion explicite en `Bool` (par exemple, `if "a"` génère une exception). Si vous souhaitez tester une chaîne non vide en Julia, vous écririez explicitement `if !isempty("")`. Peut-être de manière surprenante, en Python `if "False"` et `bool("False")` évaluent tous deux à `True` (car `"False"` est une chaîne non vide) ; en Julia, `parse(Bool, "false")` renvoie `false`.
  * En Julia, un nouveau scope local est introduit par la plupart des blocs de code, y compris les boucles et `try` — `catch` — `finally`. Notez que les compréhensions (liste, générateur, etc.) introduisent un nouveau scope local à la fois en Python et en Julia, tandis que les blocs `if` n'introduisent pas de nouveau scope local dans les deux langages.

## Noteworthy differences from C/C++

  * Les tableaux Julia sont indexés avec des crochets, et peuvent avoir plus d'une dimension `A[i,j]`. Cette syntaxe n'est pas juste un sucre syntaxique pour une référence à un pointeur ou une adresse comme en C/C++. Voir [the manual entry about array construction](@ref man-multi-dim-arrays).
  * En Julia, l'indexation des tableaux, des chaînes, etc. est basée sur 1 et non sur 0.
  * Les tableaux Julia ne sont pas copiés lorsqu'ils sont assignés à une autre variable. Après `A = B`, modifier les éléments de `B` modifiera également `A`. Les opérateurs de mise à jour comme `+=` n'opèrent pas sur place, ils sont équivalents à `A = A + B` qui réaffecte le côté gauche au résultat de l'expression du côté droit.
  * Les tableaux Julia sont en ordre de colonne (ordonnés Fortran) tandis que les tableaux C/C++ sont par défaut en ordre de ligne. Pour obtenir des performances optimales lors de la boucle sur les tableaux, l'ordre des boucles doit être inversé dans Julia par rapport à C/C++ (voir [relevant section of Performance Tips](@ref man-performance-column-major)).
  * Les valeurs de Julia ne sont pas copiées lorsqu'elles sont assignées ou passées à une fonction. Si une fonction modifie un tableau, les changements seront visibles dans l'appelant.
  * En Julia, les espaces blancs sont significatifs, contrairement à C/C++, il faut donc faire attention lors de l'ajout ou de la suppression d'espaces dans un programme Julia.
  * En Julia, les nombres littéraux sans point décimal (comme `42`) créent des entiers signés, de type `Int`, mais les littéraux trop grands pour tenir dans la taille du mot machine seront automatiquement promus à un type de taille plus grande, comme `Int64` (si `Int` est `Int32`), `Int128`, ou le type arbitrairement grand `BigInt`. Il n'y a pas de suffixes littéraux numériques, tels que `L`, `LL`, `U`, `UL`, `ULL` pour indiquer signé et/ou non signé. Les littéraux décimaux sont toujours signés, et les littéraux hexadécimaux (qui commencent par `0x` comme en C/C++), sont non signés, sauf lorsqu'ils encodent plus de 128 bits, auquel cas ils sont de type `BigInt`. Les littéraux hexadécimaux ont également, contrairement à C/C++/Java et contrairement aux littéraux décimaux en Julia, un type basé sur la *longueur* du littéral, y compris les 0s en tête. Par exemple, `0x0` et `0x00` ont le type [`UInt8`](@ref), `0x000` et `0x0000` ont le type [`UInt16`](@ref), puis les littéraux avec 5 à 8 chiffres hexadécimaux ont le type `UInt32`, 9 à 16 chiffres hexadécimaux le type `UInt64`, 17 à 32 chiffres hexadécimaux le type `UInt128`, et plus de 32 chiffres hexadécimaux le type `BigInt`. Cela doit être pris en compte lors de la définition de masques hexadécimaux, par exemple `~0xf == 0xf0` est très différent de `~0x000f == 0xfff0`. Les littéraux `Float64` 64 bits et [`Float32`](@ref) 32 bits sont exprimés respectivement comme `1.0` et `1.0f0`. Les littéraux à virgule flottante sont arrondis (et non promus au type `BigFloat`) s'ils ne peuvent pas être représentés exactement. Les littéraux à virgule flottante se comportent de manière plus proche de C/C++. Les littéraux octaux (préfixés par `0o`) et binaires (préfixés par `0b`) sont également traités comme non signés (ou `BigInt` pour plus de 128 bits).
  * En Julia, l'opérateur de division [`/`](@ref) renvoie un nombre à virgule flottante lorsque les deux opérandes sont de type entier. Pour effectuer une division entière, utilisez [`div`](@ref) ou [`÷`](@ref div).
  * L'indexation d'un `Array` avec des types à virgule flottante est généralement une erreur en Julia. L'équivalent Julia de l'expression C `a[i / 2]` est `a[i ÷ 2 + 1]`, où `i` est de type entier.
  * Les littéraux de chaîne peuvent être délimités par `"` ou `"""`, les littéraux délimités par `"""` peuvent contenir des caractères `"` sans les citer comme `"\""`. Les littéraux de chaîne peuvent avoir des valeurs d'autres variables ou expressions interpolées dans eux, indiquées par `$nomdevariable` ou `$(expression)`, ce qui évalue le nom de la variable ou l'expression dans le contexte de la fonction.
  * `//` indique un [`Rational`](@ref) nombre, et non un commentaire sur une seule ligne (qui est `#` en Julia)
  * `#=` indique le début d'un commentaire multilignes, et `=#` le termine.
  * Les fonctions en Julia renvoient des valeurs à partir de leur dernière expression ou du mot-clé `return`. Plusieurs valeurs peuvent être renvoyées par les fonctions et assignées sous forme de tuples, par exemple `(a, b) = mafonction()` ou `a, b = mafonction()`, au lieu de devoir passer des pointeurs vers des valeurs comme on devrait le faire en C/C++ (c'est-à-dire `a = mafonction(&b)`).
  * Julia ne nécessite pas l'utilisation de points-virgules pour terminer les instructions. Les résultats des expressions ne sont pas automatiquement imprimés (sauf à l'invite interactive, c'est-à-dire le REPL), et les lignes de code n'ont pas besoin de se terminer par des points-virgules. [`println`](@ref) ou [`@printf`](@ref) peuvent être utilisés pour imprimer une sortie spécifique. Dans le REPL, `;` peut être utilisé pour supprimer la sortie. `;` a également une signification différente dans `[ ]`, quelque chose à surveiller. `;` peut être utilisé pour séparer des expressions sur une seule ligne, mais ne sont pas strictement nécessaires dans de nombreux cas, et sont plus une aide à la lisibilité.
  * En Julia, l'opérateur [`⊻`](@ref xor) ([`xor`](@ref)) effectue l'opération XOR bit à bit, c'est-à-dire [`^`](@ref) en C/C++. De plus, les opérateurs bit à bit n'ont pas la même priorité qu'en C/C++, donc des parenthèses peuvent être nécessaires.
  * Le [`^`](@ref) de Julia est l'exponentiation (pow), pas le XOR bit à bit comme en C/C++ (utilisez [`⊻`](@ref xor), ou [`xor`](@ref), en Julia)
  * Julia a deux opérateurs de décalage à droite, `>>` et `>>>`. `>>` effectue un décalage arithmétique, `>>>` effectue toujours un décalage logique, contrairement à C/C++, où la signification de `>>` dépend du type de la valeur étant décalée.
  * Le `->` de Julia crée une fonction anonyme, il n'accède pas à un membre via un pointeur.
  * Julia ne nécessite pas de parenthèses lors de l'écriture des instructions `if` ou des boucles `for`/`while` : utilisez `for i in [1, 2, 3]` au lieu de `for (int i=1; i <= 3; i++)` et `if i == 1` au lieu de `if (i == 1)`.
  * Julia ne traite pas les nombres `0` et `1` comme des booléens. Vous ne pouvez pas écrire `if (1)` en Julia, car les instructions `if` n'acceptent que des booléens. Au lieu de cela, vous pouvez écrire `if true`, `if Bool(1)`, ou `if 1==1`.
  * Julia utilise `end` pour indiquer la fin des blocs conditionnels, comme `if`, des blocs de boucle, comme `while`/ `for`, et des fonctions. Au lieu de la syntaxe `if ( cond ) statement` sur une seule ligne, Julia permet des instructions sous la forme `if cond; statement; end`, `cond && statement` et `!cond || statement`. Les instructions d'assignation dans ces deux dernières syntaxes doivent être explicitement enveloppées entre parenthèses, par exemple `cond && (x = value)`, en raison de la priorité des opérateurs.
  * Julia n'a pas de syntaxe de continuation de ligne : si, à la fin d'une ligne, l'entrée jusqu'à présent est une expression complète, elle est considérée comme terminée ; sinon, l'entrée continue. Une façon de forcer une expression à continuer est de l'envelopper dans des parenthèses.
  * Les macros Julia opèrent sur des expressions analysées, plutôt que sur le texte du programme, ce qui leur permet d'effectuer des transformations sophistiquées du code Julia. Les noms de macro commencent par le caractère `@`, et ont à la fois une syntaxe semblable à celle des fonctions, `@mymacro(arg1, arg2, arg3)`, et une syntaxe semblable à celle des instructions, `@mymacro arg1 arg2 arg3`. Les formes sont interchangeables ; la forme semblable à celle des fonctions est particulièrement utile si la macro apparaît dans une autre expression, et est souvent la plus claire. La forme semblable à celle des instructions est souvent utilisée pour annoter des blocs, comme dans la construction `for` distribuée : `@distributed for i in 1:n; #= corps =#; end`. Lorsque la fin de la construction de la macro peut être floue, utilisez la forme semblable à celle des fonctions.
  * Julia a un type d'énumération, exprimé à l'aide de la macro `@enum(nom, valeur1, valeur2, ...)` Par exemple : `@enum(Fruit, banane=1, pomme, poire)`
  * Par convention, les fonctions qui modifient leurs arguments ont un `!` à la fin du nom, par exemple `push!`.
  * En C++, par défaut, vous avez une dispatch statique, c'est-à-dire que vous devez annoter une fonction comme virtuelle pour avoir une dispatch dynamique. D'autre part, en Julia, chaque méthode est "virtuelle" (bien que ce soit plus général que cela puisque les méthodes sont dispatchées sur chaque type d'argument, pas seulement `this`, en utilisant la règle de la déclaration la plus spécifique).

### Julia ⇔ C/C++: Namespaces

  * Les `namespace`s en C/C++ correspondent à peu près aux `module`s en Julia.
  * Il n'y a pas de variables ou de champs privés en Julia. Tout est accessible publiquement via des chemins entièrement qualifiés (ou des chemins relatifs, si désiré).
  * `using MyNamespace::myfun` (C++) correspond à peu près à `import MyModule: myfun` (Julia).
  * `using namespace MyNamespace` (C++) correspond à peu près à `using MyModule` (Julia)

      * En Julia, seuls les symboles `export`és sont rendus disponibles au module appelant.
      * En C++, seuls les éléments trouvés dans les fichiers d'en-tête inclus (publics) sont rendus disponibles.
  * Avertissement : les mots-clés `import`/`using` (Julia) *chargent* également des modules (voir ci-dessous).
  * Avertissement : `import`/`using` (Julia) ne fonctionne qu'au niveau de la portée globale (`module`s)

      * En C++, `using namespace X` fonctionne dans des portées arbitraires (ex : portée de fonction).

### Julia ⇔ C/C++: Module loading

  * Lorsque vous pensez à une "**bibliothèque**" C/C++, vous recherchez probablement un "**package**" Julia.

      * Avertissement : Les bibliothèques C/C++ abritent souvent plusieurs "modules logiciels", tandis que les "packages" Julia abritent généralement un seul.
      * Rappel : Les `modules` Julia sont des portées globales (pas nécessairement des "modules logiciels").
  * **Au lieu de scripts build/`make`**, Julia utilise des "Environnements de Projet" (parfois appelés soit "Projet" soit "Environnement").

      * Les scripts de construction ne sont nécessaires que pour des applications plus complexes (comme celles nécessitant de compiler ou de télécharger des exécutables C/C++).
      * Pour développer une application ou un projet en Julia, vous pouvez initialiser son répertoire racine en tant qu'« Environnement de Projet » et y loger le code/packages spécifiques à l'application. Cela offre un bon contrôle sur les dépendances du projet et sur la reproductibilité future.
      * Les packages disponibles sont ajoutés à un "Environnement de Projet" avec la fonction `Pkg.add()` ou en mode REPL Pkg. (Cela ne **charge** cependant pas ledit package).
      * La liste des paquets disponibles (dépendances directes) pour un "Environnement de Projet" est enregistrée dans son fichier `Project.toml`.
      * Les informations de dépendance *complètes* pour un "Environnement de Projet" sont générées automatiquement et enregistrées dans son fichier `Manifest.toml` par `Pkg.resolve()`.
  * Les packages ("modules logiciels") disponibles dans l'"Environnement de Projet" sont chargés avec `import` ou `using`.

      * En C/C++, vous `#include <moduleheader>` pour obtenir des déclarations d'objets/fonctions, et vous liez des bibliothèques lorsque vous construisez l'exécutable.
      * En Julia, appeler `using`/`import` à nouveau ne fait que ramener le module existant dans le scope, mais ne le charge pas à nouveau (similaire à l'ajout de la directive non standard `#pragma once` en C/C++).
  * **Les dépôts de paquets basés sur des répertoires** (Julia) peuvent être rendus disponibles en ajoutant des chemins de dépôt au tableau `Base.LOAD_PATH`.

      * Les paquets provenant de dépôts basés sur des répertoires ne nécessitent pas l'outil `Pkg.add()` avant d'être chargés avec `import` ou `using`. Ils sont simplement disponibles pour le projet.
      * Les dépôts de paquets basés sur des répertoires sont la **solution la plus rapide** pour développer des bibliothèques locales de "modules logiciels".

### Julia ⇔ C/C++: Assembling modules

  * En C/C++, les fichiers `.c`/`.cpp` sont compilés et ajoutés à une bibliothèque avec des scripts de construction `make`.

      * En Julia, les instructions `import [PkgName]`/`using [PkgName]` chargent `[PkgName].jl` situé dans le sous-répertoire `[PkgName]/src/` d'un package.
      * En retour, `[PkgName].jl` charge généralement des fichiers source associés avec des appels à `include "[someotherfile].jl"`.
  * `include "./path/to/somefile.jl"` (Julia) est très similaire à `#include "./path/to/somefile.jl"` (C/C++).

      * Cependant, `include "..."` (Julia) n'est pas utilisé pour inclure des fichiers d'en-tête (non requis).
      * **Ne pas utiliser** `include "..."` (Julia) pour charger du code à partir d'autres "modules logiciels" (utilisez `import`/`using` à la place).
      * `include "path/to/some/module.jl"` (Julia) instancierait plusieurs versions du même code dans différents modules (créant des *types* (etc.) *distincts* avec les *mêmes* noms).
      * `include "somefile.jl"` est généralement utilisé pour assembler plusieurs fichiers *au sein du même package Julia* ("module logiciel"). Il est donc relativement simple de s'assurer que les fichiers sont `include`és une seule fois (pas de confusion avec `#ifdef`).

### Julia ⇔ C/C++: Module interface

  * C++ expose des interfaces en utilisant des fichiers ".h"/".hpp" "public", tandis que les `modules` Julia marquent des symboles spécifiques destinés à leurs utilisateurs comme `public` ou `export`és.

      * Souvent, les `modules` Julia ajoutent simplement des fonctionnalités en générant de nouvelles "méthodes" pour des fonctions existantes (ex : `Base.push!`).
      * Les développeurs de paquets Julia ne peuvent donc pas s'appuyer sur des fichiers d'en-tête pour la documentation des interfaces.
      * Les interfaces pour les paquets Julia sont généralement décrites à l'aide de docstrings, README.md, pages web statiques, ...
  * Certains développeurs choisissent de ne pas `exporter` tous les symboles nécessaires à l'utilisation de leur package/module, mais devraient tout de même marquer les symboles non exportés destinés aux utilisateurs comme `public`.

      * Les utilisateurs pourraient être amenés à accéder à ces composants en qualifiant les fonctions/structures/... avec le nom du package/module (ex : `MyModule.run_this_task(...)`).

### Julia ⇔ C/C++: Quick reference

| Software Concept               | Julia                                                                          | C/C++                                                     |
|:------------------------------ |:------------------------------------------------------------------------------ |:--------------------------------------------------------- |
| unnamed scope                  | `begin` ... `end`                                                              | `{` ... `}`                                               |
| function scope                 | `function x()` ... `end`                                                       | `int x() {` ... `}`                                       |
| global scope                   | `module MyMod` ... `end`                                                       | `namespace MyNS {` ... `}`                                |
| software module                | A Julia "package"                                                              | `.h`/`.hpp` files<br>+compiled `somelib.a`                |
| assembling<br>software modules | `SomePkg.jl`: ...<br>`import("subfile1.jl")`<br>`import("subfile2.jl")`<br>... | `$(AR) *.o` &rArr; `somelib.a`                            |
| import<br>software module      | `import SomePkg`                                                               | `#include <somelib>`<br>+link in `somelib.a`              |
| module library                 | `LOAD_PATH[]`, *Git repository,<br>**custom package registry                   | more `.h`/`.hpp` files<br>+bigger compiled `somebiglib.a` |

* The Julia package manager supports registering multiple packages from a single Git repository.<br> * This allows users to house a library of related packages in a single repository.<br> ** Julia registries are primarily designed to provide versioning \& distribution of packages.<br> ** Custom package registries can be used to create a type of module library.

## Noteworthy differences from Common Lisp

  * Julia utilise par défaut un indexage basé sur 1 pour les tableaux, et elle peut également gérer des [index offsets](@ref man-custom-indices) arbitraires.
  * Les fonctions et les variables partagent le même espace de noms (« Lisp-1 »).
  * Il existe un type [`Pair`](@ref), mais il n'est pas destiné à être utilisé comme un `COMMON-LISP:CONS`. Diverses collections itérables peuvent être utilisées de manière interchangeable dans la plupart des parties du langage (par exemple, splatting, tuples, etc.). Les `Tuple`s sont les plus proches des listes Common Lisp pour des collections *courtes* d'éléments hétérogènes. Utilisez des `NamedTuple`s à la place des alists. Pour des collections plus grandes de types homogènes, les `Array`s et `Dict`s doivent être utilisés.
  * Le flux de travail typique de Julia pour le prototypage utilise également une manipulation continue de l'image, mise en œuvre avec le package [Revise.jl](https://github.com/timholy/Revise.jl).
  * Pour des performances, Julia préfère que les opérations aient [type stability](@ref man-type-stability). Alors que Common Lisp s'abstrait des opérations machine sous-jacentes, Julia s'en rapproche. Par exemple :

      * La division entière utilisant `/` renvoie toujours un résultat en virgule flottante, même si le calcul est exact.

          * `//` renvoie toujours un résultat rationnel
          * `÷` renvoie toujours un résultat entier (tronqué)
      * Les bignums sont pris en charge, mais la conversion n'est pas automatique ; les entiers ordinaires [overflow](@ref faq-integer-arithmetic).
      * Les nombres complexes sont pris en charge, mais pour obtenir des résultats complexes, [you need complex inputs](@ref faq-domain-errors).
      * Il existe plusieurs types Complex et Rational, avec différents types de composants.
  * Les modules (espaces de noms) peuvent être hiérarchiques. [`import`](@ref) et [`using`](@ref) ont un double rôle : ils chargent le code et le rendent disponible dans l'espace de noms. `import` pour seulement le nom du module est possible (à peu près équivalent à `ASDF:LOAD-OP`). Les noms de slot n'ont pas besoin d'être exportés séparément. Les variables globales ne peuvent pas être assignées depuis l'extérieur du module (sauf avec `eval(mod, :(var = val))` comme échappatoire).
  * Les macros commencent par `@`, et ne sont pas aussi intégrées dans le langage que dans Common Lisp ; par conséquent, l'utilisation des macros n'est pas aussi répandue que dans ce dernier. Une forme d'hygiène pour [macros](@ref Metaprogramming) est supportée par le langage. En raison de la syntaxe de surface différente, il n'y a pas d'équivalent à `COMMON-LISP:&BODY`.
  * *Toutes* les fonctions sont génériques et utilisent le dispatch multiple. Les listes d'arguments n'ont pas besoin de suivre le même modèle, ce qui conduit à un idiome puissant (voir [`do`](@ref)). Les arguments optionnels et les arguments nommés sont gérés différemment. Les ambiguïtés de méthode ne sont pas résolues comme dans le système d'objets Common Lisp, nécessitant la définition d'une méthode plus spécifique pour l'intersection.
  * Les symboles n'appartiennent à aucun paquet et ne contiennent pas de valeurs *en soi*. `M.var` évalue le symbole `var` dans le module `M`.
  * Un style de programmation fonctionnelle est entièrement pris en charge par le langage, y compris les fermetures, mais ce n'est pas toujours la solution idiomatique pour Julia. Certains [workarounds](@ref man-performance-captured) peuvent être nécessaires pour des performances lors de la modification des variables capturées.
