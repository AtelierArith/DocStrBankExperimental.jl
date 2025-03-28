Un [`Face`](@ref) est une collection d'attributs graphiques pour afficher du texte. Les faces contrôlent la façon dont le texte est affiché dans le terminal, et peut-être aussi dans d'autres endroits.

La plupart du temps, un [`Face`](@ref) sera stocké dans les dictionnaires de faces globaux comme une association unique avec un *nom de face* Symbol, et sera le plus souvent référencé par ce nom plutôt que par l'objet [`Face`](@ref) lui-même.

# Attributs

Tous les attributs peuvent être définis via le constructeur par mot-clé, et par défaut à `nothing`.

  * `height` (un `Int` ou `Float64`): La hauteur en décimales (lorsqu'un `Int`), ou comme un facteur de la taille de base (lorsqu'un `Float64`).
  * `weight` (un `Symbol`): L'un des symboles (du plus léger au plus dense) `:thin`, `:extralight`, `:light`, `:semilight`, `:normal`, `:medium`, `:semibold`, `:bold`, `:extrabold`, ou `:black`. Dans les terminaux, tout poids supérieur à `:normal` est affiché en gras, et dans les terminaux qui supportent le texte à luminosité variable, tout poids inférieur à `:normal` est affiché comme léger.
  * `slant` (un `Symbol`): L'un des symboles `:italic`, `:oblique`, ou `:normal`.
  * `foreground` (un `SimpleColor`): La couleur de premier plan du texte.
  * `background` (un `SimpleColor`): La couleur de fond du texte.
  * `underline`, le soulignement du texte, qui prend l'une des formes suivantes :

      * un `Bool`: Si le texte doit être souligné ou non.
      * un `SimpleColor`: Le texte doit être souligné avec cette couleur.
      * un `Tuple{Nothing, Symbol}`: Le texte doit être souligné en utilisant le style défini par le Symbol, l'un de `:straight`, `:double`, `:curly`, `:dotted`, ou `:dashed`.
      * un `Tuple{SimpleColor, Symbol}`: Le texte doit être souligné dans la SimpleColor spécifiée, et en utilisant le style spécifié par le Symbol, comme précédemment.
  * `strikethrough` (un `Bool`): Si le texte doit être barré.
  * `inverse` (un `Bool`): Si les couleurs de premier plan et de fond doivent être inversées.
  * `inherit` (un `Vector{Symbol}`): Noms des faces à hériter, avec les faces antérieures prenant la priorité. Toutes les faces héritent de la face `:default`.
