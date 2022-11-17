# Test front & back

#### **information** :

<p>
    &nbsp;&nbsp;&nbsp; - Pour lire ce fichier veuillez utiliser un éditeur qui supporte les fichier Markdown. 
</p>

## **Fonctionnalités à implémenter**:

<p>
    L'application WEB vous permettra de gérer très simplement un stock contenant différents produits. Nous nous intéressons à l'état du stock (inventaire) ainsi qu'aux différent mouvements qui font entrer ou sortir certaines quantités de produit de cet inventaire.
</p>

## **_Technos attendues_**:

NodeJs, Express, Javascript ES6, Github.

## **API REST**

<p>
    La premiere partie de l'application est une API HTTP REST, on supposera que la liste des different produits possible est disponible sur le serveur sous la forme d'un fichier JSON.
    (server/products.json), l'inventaire est uniquement gardé en mémoire, ce qui signifie qu'il est vide au moment où le serveur HTTP est démarré.
</p>
<p>voici les différentes méthodes et URL qui constituent l'API</p>

## **Produits**

### **GET /products**

_Récupère la liste des produits connus du serveur._

| Code | Description                         |
| ---- | ----------------------------------- |
| 200  | liste des produits                  |
|      | Exemple:                            |
|      | `[{ id : 123, name : "Bic bleu" }]` |
|      |                                     |

## **Inventaire**

### **GET /inventory**

_Récupère l'inventaire du stock_

| Code | Description                                                      |
| ---- | ---------------------------------------------------------------- |
| 200  | liste des articles en stock.                                     |
|      | Content-type: application/json                                   |
|      | [{ productId : 123, productName : "Bic bleu", "quantity" : 35 }] |
|      |                                                                  |

## **Mouvements**

### **GET /moves**

_Récupère l'historique des mouvements d'inventaire_

| Code | Description                                                                                      |
| ---- | ------------------------------------------------------------------------------------------------ |
| 200  | liste des mouvements.                                                                            |
|      | Content-type: application/json                                                                   |
|      | Exemple : [{ productId : 123, productName : "Bic bleu", "quantity" : 35 }]                       |
|      | Astuce : utilisez la fonction toJSON() sur un objet Date pour produire la date d'enregistrement. |

### **POST /moves**

_Enregistre un mouvement_
_Lorsque le serveur reçoit une rêquete d'enregistrement, il ajoute à celle-ci la date du jour et l'heure à laquelle la requête a été reçue, il met également à jour l'inventaire, disponible via la requête GET /inventory, et la liste des mouvements, disponible via la requête GET /moves_
_Corps de la requête (obligatoire) : mouvement à enregistrer._

_Content-Type: application/JSON_

_Exemple_

` { "productId" : 123, quantity : 5, direction : "in" }`

| Code | Description                                                                             |
| ---- | --------------------------------------------------------------------------------------- |
| 201  | mouvement enregistré.                                                                   |
| 400  | mouvement invalide                                                                      |
|      | Cette réponse est donnée si :                                                           |
|      | - productId n'est pas un nombre entier positif                                          |
|      | - productId ne correspond pas à l'identifiant d'un produit connu du serveur             |
|      | - quntity n'est pas un nombre entier supérieur a 1                                      |
|      | - direction est différent de "in" ou "out"                                              |
|      | - direction est "out" et quantity est supérieur à la quantité disponible dans le stock. |

### **POST /reset**

_Vide la liste des mouvements et remet l'inventaire à Zero_

| Code | Description     |
| ---- | --------------- |
| 204  | Pas de contenu. |

## **_Contraintes techniques_**:

- _utilisation de Github est obligatoire dès le début du projet_
- _utilisation des commits lisible et régulier_
