```
var
```

Die Syntax `var"#example#"` bezieht sich auf eine Variable mit dem Namen `Symbol("#example#")`, obwohl `#example#` kein gültiger Julia-Identifikator ist.

Dies kann nützlich sein für die Interoperabilität mit Programmiersprachen, die unterschiedliche Regeln für die Konstruktion gültiger Identifikatoren haben. Zum Beispiel, um auf die `R`-Variable `draw.segments` zu verweisen, können Sie `var"draw.segments"` in Ihrem Julia-Code verwenden.

Es wird auch verwendet, um den Julia-Quellcode anzuzeigen, der durch Makro-Hygiene gegangen ist oder anderweitig Variablennamen enthält, die nicht normal geparst werden können.

Beachten Sie, dass diese Syntax Parser-Unterstützung erfordert, sodass sie direkt vom Parser erweitert wird, anstatt als normales String-Makro `@var_str` implementiert zu werden.

!!! compat "Julia 1.3"
    Diese Syntax erfordert mindestens Julia 1.3.

