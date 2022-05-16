# MySQL monitor  
------
Dans ce tutoriel nous allons voir comment utiliser MySQL dans un command prompt  
------
## Ouvrir le cmd  

Pour ouvrir le cmd il faut taper simultanément sur les touches :
<kdb>windows</kdb> + <kdb>r</kdb>  
Ceci nous ouvrira le shell dans lequel on va taper *cmd* ce qui nous permettra d'ouvrir le command prompt.  
  
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/executeCMD.PNG)  
  
Une fois le cmd ouvert il va falloir nous placer dans __MySQL__ en suivant le chemin 'C:\wamp64\bin\mysql\mysql5.7.36\bin', pour cela dans notre cmd il faudra écrire :  
```
set PATH=%PATH%; C:\wamp64\bin\mysql\mysql5.7.36\bin
```  
Un autre moyen d'aller directement dans le fichier avec cmd est d'ouvrir le fichier et de taper *cmd* dans l'url.  
  
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/Animation.gif)  
------
## Ouvrir MySQL dans le cmd  
Pour éxécuter MySQL dans le terminal, il nous faut rentrer la commande :  
### avec mot de passe
```
mysql -u root -p
```  
### sans mot de passe 
```
mysql -u root
```
  
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/cmdSqlLRoot.PNG)  
>-u pour l'utilisateur  
>-p pour le mot de passe
------
## Les bases de données  
Une base de donnée c'est un espace de stockage sous forme de tableau depuis lequel une application va pouvoir effectuer des actions.  
Une base de donnée contient des objets.  
Dans une base de donnée un objet équivaut à une table, par exemple dans une base de donnée qui rescence des véhicules la table **voiture**  vaut l'objet *voiture*.  
Pour reprendre notre exemple une **Audi** ou une **BMW** sont chacune une instance de l'objet *voiture*.  
  
>:warning: Lorsque l'on nomme les bases de données ou les tables on ne doit pas utilisé de caractères spéciaux ou d'espace.  
>Par convention les objets (nom des tables) sont au singulier.  

* Les objets sont catégorisés par leurs noms  
* Les types représentent les champs  
* Les caractéristiques des champs sont le typage de chaque champ (exple: integer)  
* Le shéma d'une table est un tableau récapitulant les caractéristiques des champs des objets  
------
## Création de la base de données  
Pour créer une base de données, il nous faudra taper la commande suivante :  
```SQL
CREATE DATABASE mydatabase;
```
Un petit message apparait pour nous indiquer que la requête a bien été éxécuter :  
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/createdatabase.png)  

Pour vérifier notre base de données on peut utliser la commande **SHOW**  
```
SHOW DATABASES;
```
Enfin pour pouvoir agir sur notre base de données (la sélectionner) on utlisera la commande :  
```SQL
USE mydatabase;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/usemydatabase.PNG)  
## Création des tables  
Pour créer une table, il nous faudra taper la commande suivante :  
```SQL
CREATE TABLE user (
    id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    nickname VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    adult BOOLEAN DEFAULT false
);
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/createTableUser.PNG)

Pour afficher et vérifier que les tables que l'on a créé précédément, on effectue la commande 
```SQL
SHOW TABLES;
```
Enfin pour afficher et vérifier tout nos champs à l'intérieur de cette table créé précédément, on effectue la commande
```
SHOW COLUMNS FROM user;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/ShowTableColumns.PNG)

### Les différents types au sein d'une table

Voici les différents types au sein d'un tableau aissgné à chaque colone et champs: 
| VARCHAR | INTEGER | BOOLEAN | FLOAT | DATE | TEXT |
|---------|---------|---------|-------|------|------|
|une chaine de caractère | nombre entier | true or false | nombre décimal | date | chaine de caractère sans limite|
------
## Intéragir avec notre base de données

Intéragir avec notre base de données nous permet de réaliser des opérations l'acronyme CRUD qui signifie : 
**create** **read** **update** **delete**.  
Toutes les commandes que nous allons voir sont dans la  
[documentation officielle](https://sql.sh/)

### Commençons par insérer des objets uniques pour alimenter notre BDD.
On utilisera la commande **INSERT INTO** qui prends en compte  
* les paramètres (nom de la table) de la tabe dans laquel on souhaite ajouter l'objet
* l'odre des colonnes (caractéristique) de l'objet
* les valeurs correspondants à chaque colonnes  

Voici un exemple de commande pour ajouter un utilisateur dans la BDD : 
```SQL
INSERT INTO `user` (`nickname`, `email`, `adult`)
VALUES ('toto', 'toto@gmail.com', true);
```
Voici un exemple où nous allons insérer plusieurs utilisateur à la fois : 
```SQL
INSERT INTO `user` (`nickname`, `email`, `adult`)
VALUES ('riri', 'riri@gmail.com', true), ('fifi', 'fifi@gmail.com', true), ('loulou', 'loulou@gmail.com', true);
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/creationUsers.png)

### Puis sélectionnons les objets dans la base de données pour afficher une lecture de nos données  
On utilisera la commande **SELECT** qui prends en compte
* Une ou plusieurs colonnes d'une table
* le nom du champ
* le nom de la table
------
Voici un exemple de commande pour lire toutes les données d'une table dans la BDD : 
```SQL
SELECT * FROM `user`;  
```
Voici un exemple où nous allons récupérer plusieurs données dans notre table de la BDD : 
```SQL
SELECT `nickname`, `email` FROM `user`;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/selectuser.PNG)

Voici un exemple où je sélectionne tout les utilisateurs avec une contrainte de l'email finissant par gmail.com :  
```SQL
SELECT `email` FROM `user` 
WHERE `email` 
LIKE "%gmail.com";
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/LikeGmail.PNG)  
Voici comment mettre une contrainte sur une chaine de caractère :
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/email.png)  

Nous pouvons aussi ordonner nos objets grâce au mot clé **ORDER BY** :  
```SQL
SELECT * FROM `user` ORDER BY id DESC;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/orderby.PNG) 
------
### Ensuite mettons à jours nos informations éxistantes en base de données pour les modifier dans notre BDD : 
On utlisera la commande **UPDATE** qui prends en compte 
* les noms des champ éxistants

Voici un exemple de commande pour mettre à jour une donnée d'une table en BDD : 
```SQL
UPDATE `user`
SET `nickname` = 'toto2'
WHERE `email` = 'toto@gmail.com';
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/updateuser.PNG)

Egalement nous pouvons metre à jours plusieurs ligne de la table de la base de données :  
```SQL
UPDATE `user`
SET `nickname` = 'riri1', `email` = 'riri1@gmail.com'
WHERE `id` = 2;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/updatealldata.PNG) 
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/tableupdate.PNG) 

### Enfin effaçons les objets sélectionnés dans notre base de données : 
on utilisera la commande **DELETE** qui prends en compte
* les lignes d'une table

Voici un exemple de commande pour supprimer une donnée d'une table en BDD :  
```SQL
DELETE FROM `user`
WHERE `id` = 1;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/delete.PNG)

Nous pouvons aussi supprimer tout les utilisateurs d'une table
```SQL
DELETE * FROM `user`
```
----------
## Les fonctions d'agrégations statiques

Les fonctions d’agrégation sont des fonctions idéales pour effectuer quelques statistiques de bases sur des tables. Les principales fonctions sont les suivantes :

::: tip
AVG() pour calculer la moyenne sur un ensemble d’enregistrement
:::

:::tip
COUNT() pour compter le nombre d’enregistrement sur une table ou une colonne distincte
:::

::: tip
MAX() pour récupérer la valeur maximum d’une colonne sur un ensemble de ligne
:::

::: tip
MIN() pour récupérer la valeur minimum de la même manière que MAX()
:::

::: tip
SUM() pour calculer la somme sur un ensemble d’enregistrement
:::

:::
Cela permet de calculer une valeur moyenne sur un ensemble de données
:::

### La fonction d'agrégation SQL AVG

On utilsera la commande **AVG** qui prends en compte
* toutes les données d'une table à savoir une colonne sélectionnée

Voici un exemple de commande où nous allons calculer la moyenne de consommation urbaine de toutes les voitures :
```SQL
SELECT AVG(`city_oil_consumption`) FROM car;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/consocar.PNG)

Egalement nous pouvons sélectionner les données d'une table par groupe pour spécifier un groupe spécifier (chaque client/utilisateur) :
```SQL
SELECT AVG(`city_oil_consumption`) FROM car GROUP BY nickname; /////////////////::A FAIRE POUR VILLE ET ROUTE sur 1 VEHICULE////// 
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/consocar.PNG)

### La fonction d'agrégation SQL COUNT

On utilisera la commande **COUNT** qui prends en compte
* Toutes les données dans une table additionnée 

Voici un exemple pour connaitre le nombre de ligne total dans une table :
```SQL
SELECT COUNT(*) FROM car;
```
Par exemple pour connaitre le nombre de ligne total sur le la colonne prix, nous effectuons la requête suivante:
```SQL
SELECT COUNT (`price`) FROM car;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/count.PNG)

### La fonction d'agrégation SQL MAX

On utilisera la commande **MAX** qui prends en compte
* La donnée maximale dans une table sélectionnée 

Cela permet de retourner la valeur maximum d’une colonne sur un ensemble de ligne à la fois pour des données numériques ou alphanumérique : 
```SQL
SELECT MAX(NOM DE LA COLONNE) FROM NOM DE LA table;
```
Par exemple pour voir la voiture la plus consommatrice sur la route nous effectuons la requête suivante: 
```SQL
SELECT MAX(`road_oil_consumption`) FROM car; ////AFFICHER QUEL VOITURE CONSOMME LE +
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/max.PNG)

### La fonction d'agrégation SQL MIN

On utilisera la commande **MIN** qui prends en compte
* La donnée mminimale dans une table sélectionnée 

Cela permet de retourner la valeur minimale d’une colonne sur un ensemble de ligne à la fois pour des données numériques ou alphanumérique : 
```SQL
SELECT MIN(NOM DE LA COLONNE) FROM NOM DE LA table; ////AFFICHER QUEL VOITURE CONSOMME LE -
```
Par exemple pour voir la voiture la plus consommatrice sur la route nous effectuons la requête suivante:
```SQL
SELECT MIN(`road_oil_consumption`) FROM car;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/min.PNG)

### La fonction d'agrégation SQL SUM

On utilsera la commande **SUM** qui prends en compte
* toutes les données additionnées d'une table à savoir sur une colonne de données numériques sélectionnée

Cela permet permet de calculer la somme totale d’une colonne contenant des valeurs numériques.
```SQL
SELECT SUM(NOM DE LA COLONNE) FROM NOM DE LA table;
```
Voici un exemple de commande où nous allons calculer la somme totale des prix de toute les voitures :
```SQL
SELECT SUM(`price`) FROM car;
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/SUM.PNG)

On peut également y rajouter une condition en y spécifiant l''id concerné:
```SQL
SELECT SUM(`price`) AS prix_total FROM car WHERE id = 1;   /////lier table pour ajouter une jointure avec USER
```
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/sumid.PNG)

------

## La requête SQL ALTER TABLE

La commande ALTER TABLE en SQL permet de modifier une table existante. Idéal pour ajouter une colonne, supprimer une colonne ou modifier une colonne existante, par exemple pour changer le type, ou même la renomer et ajouter une clé étrangère bref les possibilités sont nombreuses.

On utilisera également la commande ALTER TABLE pour lier plusieurs tables entre-elles, en effet cela nous permet d'établir une relation à double sens: 

En effet nous pouvons avoir du "Many to One" ou "One to Many" car la relation est bi-drectionnelles.

Voic la commande a effectuée: 
```SQL
ALTER TABLE `NOM DE LA TABLE` ADD FOREIGN KEY (`CHAMP DE LA TABLE`) REFERENCES NOM DE LA TABLE(id) ON DELETE CASCADE;
```
Par exemple notre table **BRAND** incluant le champ *NAME* en l'ocurence *Audi* peut avoir plusieurs modèles soit *brand_id* de notre table **CAR** donc une Audi peut être une Audi A3, une Audi TT RS5 coupe sport, ou une Audi R8 coupe V10.

Voici comment nous procédons concrètement (voir screen shot ci dessous):
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/altertableCAR.PNG)

## Ajouter un champ dans une table SQL ALTER TABLE

Afin de pouvoir effectuer ds liasons entre les tables il nous ajouter un champ à celui-ci.
Par exemple nous ajoutons un champ nommé dans la table **USER** pour que celui-ci soit rélié à la table **CAR**

Voic la commande a effectuée: 
```SQL
ALTER TABLE `user` ADD `id_user_car` INT NOT NULL;
```

Voici comment nous procédons concrètement (voir screen shot ci dessous):
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/addField.PNG)

## La fonction SQL INNER JOIN

La commande **INNER JOIN** est un type de jointure très commune pour lier plusieurs tables entres elles. cette commande retourne les enregistrements lorsqu'il y a au moins une ligne dans chaque colonne qui correspond à la condition.  

On utilisera la commande suivante :  

```SQL
SELECT * FROM CAR INNER JOIN Brand ON brand_id = brand.id;
```  
![img shell](https://github.com/Hakimcdl/mySQL/blob/main/img/innerjoinBrandid.PNG)

## La requête SQL INNER JOIN

Afin de créer l'inner join une table intermédiraire a été créé appelé **users_cars** permettant de créer 2 clés étrangères sur cette même table intermédiaire afin de les joindre aux 2 autres tables concernée à savoir **USER** et **CAR**.

On utlisera la commande suivante: 
```SQL
 CREATE TABLE users_cars (id_user INTEGER NOT NULL, id_car INTEGER NOT NULL);
```  
1er action effectué la création de la table intermédiaire
![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/creationtablejointure.PNG)

puis 2ème action effectuée c'est à dire l'affection des clés étrangères:

On utlisera la commande suivante pour la 1ère clés: 

```SQL
ALTER TABLE `users_cars` ADD FOREIGN KEY (`id_user`) REFERENCES car(id) ON DELETE CASCADE;
```  

On utlisera la commande suivante pour la 2ème clés: 

```SQL
ALTER TABLE `users_cars` ADD FOREIGN KEY (`id_car`) REFERENCES user(id) ON DELETE CASCADE;
```

Ainsi cela permet de créer les liens MANY TO MANY entre plusieurs utilisateurs et plusieurs voitures: 
Voici un sceenshot démonstratif montrant la jointure de celui-ci via la table de jointure:

![image Shell](https://github.com/Thomas17130/mySql/blob/main/img/foreignkeiid.PNG)