Ein [`Face`](@ref) ist eine Sammlung grafischer Attribute zur Anzeige von Text. Faces steuern, wie Text im Terminal und möglicherweise auch an anderen Orten angezeigt wird.

Die meiste Zeit wird ein [`Face`](@ref) in den globalen Faces-Dictionaries als einzigartige Zuordnung zu einem *Face-Namen* Symbol gespeichert und wird am häufigsten unter diesem Namen anstelle des [`Face`](@ref) Objekts selbst referenziert.

# Attribute

Alle Attribute können über den Schlüsselwort-Konstruktor gesetzt werden und standardmäßig auf `nothing` gesetzt.

  * `height` (ein `Int` oder `Float64`): Die Höhe entweder in dezi-pt (wenn ein `Int`), oder als Faktor der Basisgröße (wenn ein `Float64`).
  * `weight` (ein `Symbol`): Eines der Symbole (von am schwächsten bis am stärksten) `:thin`, `:extralight`, `:light`, `:semilight`, `:normal`, `:medium`, `:semibold`, `:bold`, `:extrabold` oder `:black`. In Terminals wird jedes Gewicht größer als `:normal` als fett angezeigt, und in Terminals, die variabel hellen Text unterstützen, wird jedes Gewicht kleiner als `:normal` als schwach angezeigt.
  * `slant` (ein `Symbol`): Eines der Symbole `:italic`, `:oblique` oder `:normal`.
  * `foreground` (eine `SimpleColor`): Die Vordergrundfarbe des Textes.
  * `background` (eine `SimpleColor`): Die Hintergrundfarbe des Textes.
  * `underline`, die Unterstreichung des Textes, die eine der folgenden Formen annimmt:

      * ein `Bool`: Ob der Text unterstrichen werden soll oder nicht.
      * eine `SimpleColor`: Der Text sollte mit dieser Farbe unterstrichen werden.
      * ein `Tuple{Nothing, Symbol}`: Der Text sollte mit dem Stil unterstrichen werden, der durch das Symbol festgelegt ist, eines von `:straight`, `:double`, `:curly`, `:dotted` oder `:dashed`.
      * ein `Tuple{SimpleColor, Symbol}`: Der Text sollte in der angegebenen SimpleColor unterstrichen werden und den zuvor durch das Symbol festgelegten Stil verwenden.
  * `strikethrough` (ein `Bool`): Ob der Text durchgestrichen werden soll.
  * `inverse` (ein `Bool`): Ob die Vordergrund- und Hintergrundfarben invertiert werden sollen.
  * `inherit` (ein `Vector{Symbol}`): Namen von Faces, von denen geerbt werden soll, wobei frühere Faces Priorität haben. Alle Faces erben von dem `:default` Face.
