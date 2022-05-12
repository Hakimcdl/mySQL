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
## ouvrir MySQL dans le cmd  
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
