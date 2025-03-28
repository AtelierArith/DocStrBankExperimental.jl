```
process_messages(r_stream::IO, w_stream::IO, incoming::Bool=true)
```

Appelé par les gestionnaires de cluster utilisant des transports personnalisés. Il doit être appelé lorsque l'implémentation du transport personnalisé reçoit le premier message d'un travailleur distant. Le transport personnalisé doit gérer une connexion logique au travailleur distant et fournir deux objets `IO`, un pour les messages entrants et l'autre pour les messages adressés au travailleur distant. Si `incoming` est `true`, le pair distant a initié la connexion. Celui des deux qui initie la connexion envoie le cookie du cluster et son numéro de version Julia pour effectuer la poignée de main d'authentification.

Voir aussi [`cluster_cookie`](@ref).
