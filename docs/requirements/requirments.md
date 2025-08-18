## Objectif
Le projet a pour but de developper un outil permetant a un utilisateur de déployer un service pour attirer un attaquant et observer ses interactions avec le service. L'outil se met en place nativement tant dis que le service repliqué lui sera contenerisé. Toutes les interactions de l'attaquants sont en permanance envoyé du docker vers la machine cliente puis enregistré dans une DB.

## Functional requirements
- Créer/démarrer un conteneur pour que l'attaquant puisse interagire avec un service
- Récolter en continue (simultanément) les interactions de l'atk avec le service
- Enregistrer les interactions l'atk dans une DB
- Ajouter un nouveau service a honeypoter
- Supprimer un service deja mis en place
- Une fois que l'atk n'utilise plus le service le conteneur associé doit être arreté
- Associer une certaine image docker pour un nouveau service, cette image sera ensuite utilisée pour créer/lancer un contenaire pour simuler le service en question

## Non-functional requirments
- Le conteneur créer lié au service doit se déployer en ... secondes
- Besoin d'une DB pour logger les interactions de l'atk 
- 
- 
