# Fetch

La méthode `fetch()` permet de faire des requêtes HTTP pour récupérer des ressources sur un serveur distant (API web par exemple). 
La méthode `fetch()` fonctionne en asynchrone c'est à dire qu'on envoie la requête au serveur mais notre code continue de s'exécuter même s'il n'a pas obtenu la réponse. C'est pour ça que `fetch()` fonctionne avec des promesses. Quand on fait une requête `fetch()`, on ne reçoit pas la réponse tout de suite : on reçoit un objet `Promises` qui aide à gérer les opérations asynchrones. Cet objet comporte trois états : pending - fulfilled - rejected et empêche le code suivant de s'éxecuter tant qu'une réponse n'a pas été reçue.

* L'état `pending` correspond à l'état initial de la promesse.
* L'état `fullfilled` intervient si l'opération demandée dans la requête à réussi.
* L'état `rejected` intervient si l'opération à échoué. 


Par exemple dans ton projet si on fait une demande pour récupérer toutes les cartes du deck ça se présentera ainsi : 

```js
fetch('http://localhost:1234/deck') // pending
  .then (response => {
    // fullfilled
    // On attent grâce au `then` que la réponse arrive
    // une fois arrivé 'response' contient la réponse du serveur 
    // Puis on peut utiliser cette réponse pour l'afficher, la partager
  })
  .catch(error => {
    // rejected
    // ce qu'il se passe en cas d'erreur 
    // si je n'arrive pas à obtenir toute les cartes du deck par exemple
  })

```

La méthode `then()` va permettre d'attendre que la réponse arrive sans que la suite du code ne s'éxecute. Dans le cas où on reçoit la réponse, on peut ensuite la manipuler. 
On peut enchainer les méthodes `then()` par exemple : 

```js 
fetch('http://localhost:1234/deck')
  .then (response => {
    response.json()
    // on récupère les données JSON de la réponse
  })
  .then (data => {
    console.log(data)
    // on affiche les données dans la console
  })
  .catch(error => {
    console.error('Erreur :', error)
  })

```
Si on ne reçoit pas de `response` on gérera l'erreur avec la méthode `catch()`

Il est possible d'ajouter des options de configuration à la requête comme les différentes méthode HTTP (GET, POST, PATCH, ... ). A ce moment là on peut configurer `fetch()` de cette façon : 
```js
fetch('http://localhost:3000/deck/add/:id',{
  method: 'POST', // le type de requête HTTP
  headers: { // se sont les en-têtes inclus dans la requête, ils permettent d'envoyer des informations supplémentaires à la requête
    'Content-Type': 'application/json', // indique que le contenu de la requête est au format JSON
    // Il existe d'autres en-têtes comme : 
    'Authorization': 'Bearer access_token' // utilisé pour les json Web Token quand on a besoin de s'authentifier par exemple
  },
  body: JSON.stringify({key: 'value'}) // les données envoyées au serveur, on précise qu'elles sont converties au format JSON
}) 
```