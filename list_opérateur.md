 ## Liste opérateur
 
```js
    $lookup //permet de faire des jointure
    $addField // creer un nouveau champs
    $unwind //decomposer les elements du tableau (affiche autant d'objet que de valeur dans la tableau)
    $project //permet d'afficher ce que nous allons voir en resultat
    $sortByCount // trier et compter
    $buckets // regroupe les documents
    $cond // mettre une condition
    $gt // superieur mais ne prend pas la valeur
    $gte // 50 et plus egal ou superieur
    $exists //verification d'une infomation (valeur true false 1 ou 0)
    $size // savoir la taille
    $mod // modulo pour savoir si quelque chose est pair ou impair
    $eq  // equal
    $not //pas equal n'ayant pas
    $lt // inferieur
    $lte // inferieur ou egal
    $nin //n'ayant ni un ni l'autre
    $expr // ecrire une expression
    $regex //filtre regex
    $multiply // faire des multiplication
    $sum // addition
    $subtract // soustraction
    $push // ajout valeur tableau
    $type // retourne la valeur type
    $where //transmettre un chaine avec  expression js
    $sort // permet de faire un trie
    $near //pas de différence avec `$nearSphere`
    $nearSphere// donner les point les plus proche geospatiaux
    $geoWithin // permet de faire une zone est de voir qu'elle point est dans la salle
    $each // transformer en tableau
    $in // dans exemple dans styles il y a blues et soul
    //exemple  
    "styles": {$in: {"blues", "soul"}}
 
 
 
    //Operateur logique
    $or // que la valeur est egal
    $nor // A ne pas utiliser
    $all //affiche toute les informations comportement les specifications
 
```
 
 
 
 
```js
    .find({}) //Permet de faire des recherches
    .insertOne({}), .insertMany({}) // permettre d'inserer des elements
    db.createCollections()//creer une collection
    db.colllections.drop()//Supprimer une collection
    db.employees.aggregate([])// Faire plusieurs chose en meme temps filtre trier ...
    db.employees.updateMany({}) .updateOne({}) // permettre de modifier des informations dans une collection
 
```