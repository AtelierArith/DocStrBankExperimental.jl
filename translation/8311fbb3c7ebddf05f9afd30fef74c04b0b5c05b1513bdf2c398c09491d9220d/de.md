```
@r_str -> Regex
```

Konstruiere einen Regex, wie `r"^[a-z]*$"`, ohne Interpolation und Unescaping (außer für das Anführungszeichen `"` welches weiterhin escaped werden muss). Der Regex akzeptiert auch ein oder mehrere Flags, die nach dem abschließenden Anführungszeichen aufgeführt sind, um sein Verhalten zu ändern:

  * `i` aktiviert die Groß-/Kleinschreibung ignorierende Übereinstimmung
  * `m` behandelt die Tokens `^` und `$` als Übereinstimmung mit dem Anfang und Ende einzelner Zeilen, anstatt mit dem gesamten String.
  * `s` erlaubt es dem `.` Modifikator, Zeilenumbrüche zu matchen.
  * `x` aktiviert den "freien Modus": Whitespace zwischen Regex-Tokens wird ignoriert, es sei denn, er ist mit `\` escaped, und `#` im Regex wird als Beginn eines Kommentars behandelt (der bis zum Zeilenende ignoriert wird).
  * `a` aktiviert den ASCII-Modus (deaktiviert `UTF` und `UCP` Modi). Standardmäßig matchen `\B`, `\b`, `\D`, `\d`, `\S`, `\s`, `\W`, `\w` usw. basierend auf Unicode-Zeicheneigenschaften. Mit dieser Option matchen diese Sequenzen nur ASCII-Zeichen. Dies schließt `\u` ein, das den angegebenen Zeichenwert direkt als ein einzelnes Byte ausgibt und nicht versucht, es in UTF-8 zu kodieren. Wichtig ist, dass diese Option das Matching gegen ungültige UTF-8-Strings ermöglicht, indem sowohl Matcher als auch Ziel als einfache Bytes behandelt werden (als wären sie ISO/IEC 8859-1 / Latin-1 Bytes) anstatt als Zeichencodierungen. In diesem Fall wird diese Option oft mit `s` kombiniert. Diese Option kann weiter verfeinert werden, indem das Muster mit (*UCP) oder (*UTF) beginnt.

Siehe [`Regex`](@ref), wenn Interpolation benötigt wird.

# Beispiele

```jldoctest
julia> match(r"a+.*b+.*?d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

Dieser Regex hat die ersten drei Flags aktiviert.
