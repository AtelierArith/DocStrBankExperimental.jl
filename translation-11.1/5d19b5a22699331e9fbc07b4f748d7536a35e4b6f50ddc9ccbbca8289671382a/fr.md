```
verify_host(url::AbstractString, [transport::AbstractString]) :: Bool
```

La fonction `verify_host` indique à l'appelant si l'identité d'un hôte doit être vérifiée lors de la communication via des transports sécurisés comme TLS ou SSH. L'argument `url` peut être :

1. une URL correcte commençant par `proto://`
2. un nom d'hôte nu de style `ssh` ou un nom d'hôte précédé de `user@`
3. un hôte de style `scp` comme ci-dessus, suivi de `:` et d'un emplacement de chemin

Dans chaque cas, la partie nom d'hôte est extraite et la décision de vérifier ou non est prise uniquement sur la base du nom d'hôte, sans tenir compte d'autre chose concernant l'URL d'entrée. En particulier, le protocole de l'URL n'a pas d'importance (plus de détails ci-dessous).

L'argument `transport` indique le type de transport dont il est question. Les valeurs actuellement connues sont `SSL`/`ssl` (alias `TLS`/`tls`) et `SSH`/`ssh`. Si le transport est omis, la requête renverra `true` uniquement si le nom d'hôte ne doit pas être vérifié, quel que soit le transport.

Le nom d'hôte est comparé aux modèles d'hôte dans les variables d'environnement pertinentes en fonction de la présence de `transport` et de sa valeur :

  * `JULIA_NO_VERIFY_HOSTS` — hôtes qui ne doivent pas être vérifiés pour aucun transport
  * `JULIA_SSL_NO_VERIFY_HOSTS` — hôtes qui ne doivent pas être vérifiés pour SSL/TLS
  * `JULIA_SSH_NO_VERIFY_HOSTS` — hôtes qui ne doivent pas être vérifiés pour SSH
  * `JULIA_ALWAYS_VERIFY_HOSTS` — hôtes qui doivent toujours être vérifiés

Les valeurs de chacune de ces variables sont une liste séparée par des virgules de modèles de noms d'hôtes avec la syntaxe suivante — chaque modèle est divisé sur `.` en parties et chaque partie doit être l'une des suivantes :

1. Un composant de nom de domaine littéral composé d'une ou plusieurs lettres ASCII, chiffres, tirets ou traits de soulignement (techniquement pas partie d'un nom d'hôte légal, mais parfois utilisé). Un composant de nom de domaine littéral ne correspond qu'à lui-même.
2. Un `**`, qui correspond à zéro ou plusieurs composants de nom de domaine.
3. Un `*`, qui correspond à n'importe quel composant de nom de domaine.

Lors de la correspondance d'un nom d'hôte avec une liste de modèles dans l'une de ces variables, le nom d'hôte est divisé sur `.` en composants et cette séquence de mots est comparée au modèle : un modèle littéral correspond exactement à un composant de nom d'hôte avec cette valeur ; un modèle `*` correspond exactement à un composant de nom d'hôte avec n'importe quelle valeur ; un modèle `**` correspond à n'importe quel nombre de composants de nom d'hôte. Par exemple :

  * `**` correspond à n'importe quel nom d'hôte
  * `**.org` correspond à n'importe quel nom d'hôte dans le domaine de premier niveau `.org`
  * `example.com` correspond uniquement au nom d'hôte exact `example.com`
  * `*.example.com` correspond à `api.example.com` mais pas à `example.com` ou `v1.api.example.com`
  * `**.example.com` correspond à n'importe quel domaine sous `example.com`, y compris `example.com` lui-même, `api.example.com` et `v1.api.example.com`

```
