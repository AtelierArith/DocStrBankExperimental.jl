```
Unicode.normalize(s::AbstractString; keywords...)
Unicode.normalize(s::AbstractString, normalform::Symbol)
```

Normalisieren Sie den String `s`. Standardmäßig wird die kanonische Komposition (`compose=true`) durchgeführt, ohne die Stabilität der Unicode-Versionierung sicherzustellen (`compat=false`), was den kürzest möglichen äquivalenten String erzeugt, aber Kompositionszeichen einführen kann, die in früheren Unicode-Versionen nicht vorhanden sind.

Alternativ kann eine der vier "Normalformen" des Unicode-Standards angegeben werden: `normalform` kann `:NFC`, `:NFD`, `:NFKC` oder `:NFKD` sein. Die Normalformen C (kanonische Komposition) und D (kanonische Dekompensation) konvertieren verschiedene visuell identische Darstellungen desselben abstrakten Strings in eine einzige kanonische Form, wobei Form C kompakter ist. Die Normalformen KC und KD kanonisieren zusätzlich "Kompatibilitätsequivalente": Sie konvertieren Zeichen, die abstrakt ähnlich, aber visuell unterschiedlich sind, in eine einzige kanonische Wahl (z. B. erweitern sie Ligaturen in die einzelnen Zeichen), wobei Form KC kompakter ist.

Alternativ kann eine feinere Kontrolle und zusätzliche Transformationen durch den Aufruf von `Unicode.normalize(s; keywords...)` erreicht werden, wobei eine beliebige Anzahl der folgenden booleschen Schlüsselwortoptionen (die alle standardmäßig auf `false` gesetzt sind, außer für `compose`) angegeben werden kann:

  * `compose=false`: keine kanonische Komposition durchführen
  * `decompose=true`: stattdessen kanonische Dekompensation durchführen (`compose=true` wird ignoriert, wenn vorhanden)
  * `compat=true`: Kompatibilitätsequivalente werden kanonisiert
  * `casefold=true`: Unicode-Groß-/Kleinschreibung durchführen, z. B. für groß-/kleinsensitive String-Vergleiche
  * `newline2lf=true`, `newline2ls=true` oder `newline2ps=true`: verschiedene Zeilenumbruchssequenzen (LF, CRLF, CR, NEL) in ein Zeilenumbruchzeichen (LF), ein Zeilen-Trennzeichen (LS) oder ein Absatz-Trennzeichen (PS) konvertieren
  * `stripmark=true`: diakritische Zeichen (z. B. Akzente) entfernen
  * `stripignore=true`: Unicode's "standardmäßig ignorierbare" Zeichen (z. B. den weichen Bindestrich oder den Links-nach-Rechts-Marker) entfernen
  * `stripcc=true`: Steuerzeichen entfernen; horizontale Tabs und Seitenumbrüche werden in Leerzeichen umgewandelt; Zeilenumbrüche werden ebenfalls in Leerzeichen umgewandelt, es sei denn, ein Zeilenumwandlungs-Flag wurde angegeben
  * `rejectna=true`: einen Fehler auslösen, wenn nicht zugewiesene Codepunkte gefunden werden
  * `stable=true`: die Stabilität der Unicode-Versionierung durchsetzen (niemals Zeichen einführen, die in früheren Unicode-Versionen fehlen)

Sie können auch das Schlüsselwort `chartransform` verwenden (das standardmäßig auf `identity` gesetzt ist), um eine beliebige *Funktion* zu übergeben, die `Integer`-Codepunkte auf Codepunkte abbildet, die auf jedes Zeichen in `s` angewendet wird, während es verarbeitet wird, um beliebige zusätzliche Normalisierungen durchzuführen. Zum Beispiel können Sie durch die Übergabe von `chartransform=Unicode.julia_chartransform` einige Julia-spezifische Zeichennormalisierungen anwenden, die von Julia beim Parsen von Bezeichnern durchgeführt werden (neben der NFC-Normalisierung: `compose=true, stable=true`).

Zum Beispiel entspricht NFKC den Optionen `compose=true, compat=true, stable=true`.

# Beispiele

```jldoctest
julia> "é" == Unicode.normalize("é") #LHS: Unicode U+00e9, RHS: U+0065 & U+0301
true

julia> "μ" == Unicode.normalize("µ", compat=true) #LHS: Unicode U+03bc, RHS: Unicode U+00b5
true

julia> Unicode.normalize("JuLiA", casefold=true)
"julia"

julia> Unicode.normalize("JúLiA", stripmark=true)
"JuLiA"
```

!!! compat "Julia 1.8"
    Das Schlüsselwortargument `chartransform` erfordert Julia 1.8.

