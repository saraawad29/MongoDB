TD – Aggregation  

db.achats.insertMany([{     "nom": "Pascal",     "prenom": "Léo",     "achats": [112.29, 88.36, 72.01],     "reductions": [12.30, 2.01]  },  {     "nom": "Perez",     "prenom": "Alex",     "achats": [20.01, 296.35],     "reductions": [9.91, 0.87]  }]) 


Ecrivez un pipeline aggregation qui permet d’obtenir le total payé par personnes et arrondissez. 


Conseils: 

Utilisez l’operateur $addFields plusieurs fois 

Ajoutez des champs pour stocker: le total des achats, le total des reductions et le total final 

Utilisez des operateurs de calcul arithmetique 




    db.achats.aggregate([{
    $addFields: {
    "totalachats": {$sum: "$achats"},
    "totalreductions": {$sum: "$reductions"}
    }},
    {$addFields: {"totalpaye": {$subtract: ["$totalachats", "$totalreductions"]}}},
    {$addFields: {"totalarrondi": {$round: ["$totalpaye",2]}}},
    {$project: {"_id":0, "nom":1,"total": "$totalarrondi"}
    }]
    )