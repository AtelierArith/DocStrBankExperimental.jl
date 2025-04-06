```
dlclose(::Nothing)
```

Pour le modèle d'utilisation très courant de

```
try
    hdl = dlopen(library_name)
    ... faire quelque chose
finally
    dlclose(hdl)
end
```

Nous définissons une méthode `dlclose()` qui accepte un paramètre de type `Nothing`, afin que le code utilisateur n'ait pas à changer son comportement dans le cas où `library_name` n'a pas été trouvé.
