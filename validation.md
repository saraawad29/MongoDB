Exercice 1 
Modifiez la collection salle afin que soient dorénavant validés les documents destinés à y être insérés ; cette validation aura lieu en mode « strict » et portera sur les champs suivants :

nom sera obligatoire et devra être de type chaîne de caractères.

capacite sera obligatoire et devra être de type entier (int).

Dans le champ adresse, les champs codePostal et ville, tous deux de type chaîne de caractères, seront obligatoires.

Que constatez-vous lors de la tentative d’insertion suivante, et quelle en est la cause ?

```
db.salles.insertOne( 
{"nom": "Super salle", "capacite": 1500, "adresse": {"ville": "Musiqueville"}} 
) 
```

Que proposez-vous pour régulariser la situation ?

```js
    var rules = {
	    "nom": {
		"bsonType":"string",		
        "description": "Chaine de caractères - obligatoire"
		},
        "capacite":{
            "bsonType": "int",
            "description": "Entier - obligatoire"
        },
        "adresse.codePostal":{
            "bsonType":"string",
            "description": "Chaine de caractères - obligatoire"
        },	
        "adresse.ville":{
            "bsonType": "string",		
            "description":"Chaine de caractères - obligatoire"
        }
    }


    db.runCommand({
        "collMod": "salles",
        "validator": {
           $jsonSchema: {
                 "bsonType": "object",
                 "required": ["nom", "capacite", "adresse.codePostal","adresse.ville"],
                 "properties": rules
           }
       }
   })

```

Exercice 2

Rajoutez à vos critères de validation existants un critère supplémentaire : le champ _id devra dorénavant être de type entier (int) ou ObjectId.

Que se passe-t-il si vous tentez de mettre à jour l’ensemble des documents existants dans la collection à l’aide de la requête suivante :


    db.runCommand({
    collMod: "salles",
    validator: {
        $jsonSchema: {
        bsonType: "object",
        required: ["nom", "capacite", "adresse.codePostal", "adresse.ville"],
        properties: {
            nom: {
            bsonType: "string"
            },
            capacite: {
            bsonType: "int"
            },
            adresse: {
            bsonType: "object",
            required: ["codePostal", "ville"],
            properties: {
                codePostal: {
                bsonType: "string"
                },
                ville: {
                bsonType: "string"
                }
            }
            },
            _id: {
            bsonType: ["int", "objectId"]
            }
        }
        }
    }
    })

```
db.salles.updateMany({}, {$set: {"verifie": true}}) 
```
    on vas avoir une erreur a cause des règles de validation 

Supprimez les critères rajoutés à l’aide de la méthode delete en JavaScript

    db.runCommand({
        collMod: "salles",
        validator: {}
    })

Exercice 3

Rajoutez aux critères de validation existants le critère suivant :

Le champ smac doit être présent OU les styles musicaux doivent figurer parmi les suivants : "jazz", "soul", "funk" et "blues".

Que se passe-t-il lorsque nous exécutons la mise à jour suivante ?


db.salles.update({"_id": 3}, {$set: {"verifie": false}}) 
