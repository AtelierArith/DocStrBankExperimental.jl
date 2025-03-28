```
define_editor(fn, pattern; wait=false)
```

Définir un nouvel éditeur correspondant à `pattern` qui peut être utilisé pour ouvrir un fichier (éventuellement à un numéro de ligne donné) en utilisant `fn`.

L'argument `fn` est une fonction qui détermine comment ouvrir un fichier avec l'éditeur donné. Il doit prendre quatre arguments, comme suit :

  * `cmd` - un objet de commande de base pour l'éditeur
  * `path` - le chemin vers le fichier source à ouvrir
  * `line` - le numéro de ligne pour ouvrir l'éditeur
  * `column` - le numéro de colonne pour ouvrir l'éditeur

Les éditeurs qui ne peuvent pas s'ouvrir à une ligne spécifique avec une commande ou une colonne spécifique peuvent ignorer l'argument `line` et/ou `column`. Le rappel `fn` doit retourner soit un objet `Cmd` approprié pour ouvrir un fichier, soit `nothing` pour indiquer qu'ils ne peuvent pas éditer ce fichier. Utilisez `nothing` pour indiquer que cet éditeur n'est pas approprié pour l'environnement actuel et qu'un autre éditeur doit être tenté. Il est possible d'ajouter des hooks d'édition plus généraux qui n'ont pas besoin de lancer des commandes externes en poussant un rappel directement dans le vecteur `EDITOR_CALLBACKS`.

L'argument `pattern` est une chaîne, une expression régulière ou un tableau de chaînes et d'expressions régulières. Pour que `fn` soit appelé, l'un des motifs doit correspondre à la valeur de `EDITOR`, `VISUAL` ou `JULIA_EDITOR`. Pour les chaînes, la chaîne doit être égale à la [`basename`](@ref) du premier mot de la commande de l'éditeur, avec son extension, le cas échéant, supprimée. Par exemple, "vi" ne correspond pas à "vim -g" mais correspond à "/usr/bin/vi -m" ; elle correspond également à `vi.exe`. Si `pattern` est une regex, elle est comparée à toute la commande de l'éditeur sous forme de chaîne échappée par le shell. Un motif de tableau correspond si l'un de ses éléments correspond. Si plusieurs éditeurs correspondent, celui ajouté le plus récemment est utilisé.

Par défaut, julia n'attend pas que l'éditeur se ferme, l'exécutant en arrière-plan. Cependant, si l'éditeur est basé sur un terminal, vous voudrez probablement définir `wait=true` et julia attendra que l'éditeur se ferme avant de reprendre.

Si l'une des variables d'environnement de l'éditeur est définie, mais qu'aucune entrée d'éditeur ne correspond, l'entrée d'éditeur par défaut est invoquée :

```
(cmd, path, line, column) -> `$cmd $path`
```

Notez que de nombreux éditeurs sont déjà définis. Toutes les commandes suivantes devraient déjà fonctionner :

  * emacs
  * emacsclient
  * vim
  * nvim
  * nano
  * micro
  * kak
  * helix
  * textmate
  * mate
  * kate
  * subl
  * atom
  * notepad++
  * Visual Studio Code
  * open
  * pycharm
  * bbedit

# Exemples

Le suivant définit l'utilisation de `emacs` basé sur un terminal :

```
define_editor(
    r"\bemacs\b.*\s(-nw|--no-window-system)\b", wait=true) do cmd, path, line
    `$cmd +$line $path`
end
```

!!! compat "Julia 1.4"
    `define_editor` a été introduit dans Julia 1.4.

