```
reject(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

Rejeter le credential `payload` afin qu'il ne soit pas réutilisé lors de futures authentifications. Ne doit être appelé que lorsque l'authentification a échoué.

Le mot-clé `shred` contrôle si les informations sensibles dans le champ de credential du payload doivent être détruites. Ne doit être défini sur `false` que lors des tests.
