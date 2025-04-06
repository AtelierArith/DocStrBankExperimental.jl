```
@goto nom
```

`@goto nom` effectue un saut inconditionnel vers l'instruction à l'emplacement [`@label nom`](@ref).

`@label` et `@goto` ne peuvent pas créer de sauts vers des instructions de niveau supérieur différentes. Les tentatives entraînent une erreur. Pour utiliser quand même `@goto`, enfermez `@label` et `@goto` dans un bloc.
