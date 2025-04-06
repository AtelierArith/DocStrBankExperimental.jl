```
catch_exceptions(logger)
```

Retourne `true` si le logger doit attraper les exceptions qui se produisent lors de la construction de l'enregistrement de log. Par défaut, les messages sont attrapés.

Par défaut, toutes les exceptions sont attrapées pour empêcher la génération de messages de log de faire planter le programme. Cela permet aux utilisateurs de basculer en toute confiance des fonctionnalités peu utilisées - comme le logging de débogage - dans un système de production.

Si vous souhaitez utiliser le logging comme une piste de vérification, vous devez désactiver cela pour votre type de logger.
