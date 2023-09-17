Bonjour, 

Merci pour ton MCD, j'ai vu quelques points d'améliorations:
* je pense que tu as inversés certaines cardinalités par exemple : 
[ADDRESS] 1,1 HAS 0,N [USER]
Dans ce cas je lis : une et une seule adresse peut appartenir à zéro ou plusieurs utilisateurs. <br> 
Pourtant en lisant ton paragraphe de contextualisation, je me rends compte que tu voulais dire l'inverse. 
* Pour la relation [USER] 1,1 LIKE 1,1 [MUG] que tu notes en tant que relation `Many To Many` j'imagine que tu as inversé les notions. En effet, comme tu l'as noté ça ressemble plus à une relation `One To One`. Avec ton contexte on s'attend à avoir une relation Many To Many comme tu l'as indiqué. Tu dois donc revoir tes cardinalités à cet endroit. 
* Les cardinalités ont globalement été inversées entre tes entités. 

Je te donne un lien pour t'aider à y voir plus cair : 
* https://www.base-de-donnees.com/cardinalites/

Pour t'aider il existe plusieurs outils pour créer des MCD [Mocodo](https://www.mocodo.net/), [draw.io](https://app.diagrams.net/), [Excalidraw](https://excalidraw.com/)