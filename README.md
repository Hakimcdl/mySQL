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
  
>:[warning]:
>Lorsque l'on nomme les bases de données ou les tables on ne doit pas utilisé de caractères spéciaux ou d'espace.  
>Par convention les objets (nom des tables) sont au singulier.  

*Les objets sont catégorisés par leurs noms  
*Les types représentent les champs  
*Les caractéristiques des champs sont le typage de chaque champ (exple: integer)  
*Le shéma d'une table est un tableau récapitulant les caractéristiques des champs des objets