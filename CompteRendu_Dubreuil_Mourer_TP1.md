# TP 1 - Administration Système
Dubreuil Pierre  
Mourer Lucie

06/02/2020


## Exercice 2
### MANUEL

#### 1. A l’aide du manuel, identifiez le rôle de la commande which

`which` : renvoie le chemin des fichiers qui seraient exécuté dans l’environnement courant si argument donnés comme commande


#### 2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher le terme option dans la page de manuel de which ?

On peut chercher un terme avec `/pattern` ou `?pattern` avec pattern ce que tu cherches


#### 3. Comment quitte-t-on le manuel ?

On quitte le manuel man avec `q`


#### 4. Chaque section du manuel a une première page, qui présente le contenu de la section. Aﬀicher la première page de la section 6 ; de quoi parle cette section ?

man 6 intro : section 6 parle des jeux disponibles sur le système

### NAVIGATION

#### 1. allez dans le dossier /var/log

`cd /var/log`


#### 2. remontez dans le dossier parent (/var) en utilisant un chemin relatif

`cd ..` : parent de là où on se trouve


#### 3. retournez dans le dossier personnel

`cd ~` : revenir au home (dossier personnel)


#### 4. revenez au dossier précédent (/var) sans utiliser de chemin

`cd -` : revenir au dossier précedent sans utiliser de chemin)


#### 5. essayez d’accéder au dossier /root ; que se passe-t-il ?

#### 6. essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez  
Sans sudo on ne peut pas accéder à /root car on doit avoir les droits de superutilisateur 


#### 7. à partir de votre dossier personnel, créez l’arborescence suivante :

```bash
cd ~ 
mkdir Dossier1  
touch Dossier1/Fichier1  
mkdir Dossier2 (on est toujours dans le home)  
mkdir Dossier2/Dossier2.1  
mkdir Dossier2/Dossier2.2  
touch Dossier2/Dossier2.2/Fichier2  
touch Dossier2/Dossier2.2/Fichier3  
```


#### 8. revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis Dossier1 ; que se passe-t-il ?

`rm` pour supprimer  
`rm Dossier1/Fichier1` -> cela le supprime   
`rm Dossier1` -> pas possible c'est un répertoire


#### 9. quelle commande permet de supprimer un dossier ?

on utilise: `rmdir Dossier1` 


#### 10. que se passe-t-il quand on applique cette commande à Dossier2 ?

ça ne marche pas sur Dossier2 car il a du contenu


#### 11. Comment supprimer en une seule commande Dossier2 et son contenu ?

on utilise : `rm Dossier 2 -R`  
et -R indique l'utilisation de la récursivité qui permet de supprimer le repertoire et son contenu

### COMMANDES IMPORTANTES

#### 1. Quelle commande permet d’aﬀicher l’heure ? A quoi sert la commande time ?

`date` et `time` fait tourner les programmes et elle determine le temps d'éxécution d'une certaine commande


#### 2. Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire sur les fichiers commençant par un point ?

`ls` : affiche le contenu visible d'un répertoire   
`la` : affiche le contenu chaché d'un répertoire.   
 Les fichiers commançant par un . sont des fichiers cachés (file system..etc)


#### 3. Où se situe le programme ls ?

`which ls` ---> /usr/bin/ls


#### 4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande.

ll n'a pas d'entrée manuel  
la commande `ll` est équivalente à `ls  -alF`  


#### 5. Quelle commande permet d’aﬀicher les fichiers contenus dans le dossier/bin ?

`ls /bin`


#### 6. Que fait la commande ls .. ?

`ls ..` montre le contenu du dossier parent du répertoire de travail


#### 7. Quelle commande donne le chemin complet du dossier courant ?

`pwd` donne le chemin complet du dossier courant


#### 8. Que fait la commande echo 'yo' > plop exécutée 2 fois ?

`echo 'yo' > plop` : écrit et remplace le contenu du fichier plop par yo


#### 9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ?

`echo 'yo' >> plop` : écrit en ajoutant yo au contenu du fichier plop``


#### 10. A quoi sert la commandefile? Essayez la sur des fichiers de types différents.

`file` détermine quel est le type du fichier


#### 11. Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien titi vers ce fichier avec la commande ln toto titi. Modifiez à présent le contenu de toto et aﬀichez le contenu de titi : qu’observe-t-on? Supprimez le fichier toto; quelle conséquence cela a-t-il surtiti ?

```bash
echo 'Hello Toto !' > toto  
ln toto titi   #ln crée un lien  
echo 'Bonjour !' > toto  
less titi #contenu du titi bien modifié  
rm toto #titi existe encore et garde la valeur  de toto  
```


#### 12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le contenu detiti; quelle conséquence pourtutu? Et inversement? Supprimez le fichiertiti; quelle conséquence cela a-t-il surtutu ?

```bash
ln -s titi tutu  #création du lien symbolique
echo 'Hello Toto !' > titi #tutu est modifié également et inversement   
rm titi #tutu existe encore ainsi que le lien mais il pointe sur un objet inexistant  
```



#### 13. Aﬀichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et reprendre le défilement à l’écran ?

```bash
cat /var/log/syslog #défile le contenu du fichier  
ctrl + s #Défilement en pause  
strl + q #reprendre le défilement  
```


#### 14. Aﬀichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les lignes 10 à 20.

```bash
head -n 5 /var/log/syslog  
tail -n 15 /var/log/syslog  
head -n 20 /var/log/syslog | tail -n 10/var/log/  syslog ou sed -n '10,20p' /var/log/syslog  
```


#### 15. Que fait la commande dmesg | less ?

`dmesg | less` permet de controler le défilement de `dmesg` qui affiche le kernel ring buffer  


#### 16. Aﬀichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’aﬀicher la page de manuel de ce fichier ?

`less /etc/passwd`  base de données textuelle d'informations sur les utilisateurs qui peuvent se connecter au système.  
`man passwd` -> modifier le mot de passe d'un utilisateur  


#### 17. Aﬀichez seulement la première colonne triée par ordre alphabétique inverse

```bash
less /etc/passwd | cut  -d ":" -f 1 | sort -r
```


#### 18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seule- ment les utilisateurs connectés) ?

`wc -l /etc/passwd` : affiche le nombre d'utilisateur 



#### 19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ?

`man -k conversion | wc -l `


#### 20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine

`sudo find / -name passwd`


#### 21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null

```bash
find / -name passwd > ~/list_passwd_files.txt 2> /dev/null
```   
On utilise 2 pour récupérer les erreurs  
`dev/null`  agit comme un broyeur et il fait 0 octet son contenu est définitvement perdu


#### 22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu précédemment

```bash
grep ll * .*
```


#### 23. Utilisez la commande locate pour trouver le fichier history.log.

```bash
locate history.log  ---> /var/log/apt/history.log
```


#### 24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il? Pourquoi?

le fichier n'apparait pas car il n'a pas encore été mis à jour dans la database (qui est mise à jour tous les jours à 7h30 )  .  
Donc si on vient de le créer on ne le trouve pas avant le lendemain avec locate.


## Exercice 3


#### 1. Copiez le fichier /var/log/syslog dans votre dossier personnel sous le nom log.txt, puis ouvrez-le avec nano

`cp /var/log/syslog ~/log.txt`


#### 2. Remplacez toutes les occurrences du mot kernel par le mot noyau

```
ctrl + \  
--> kernel   
--> noyau   
--> a
```


#### 3. Déplacer les 10 premières lignes à la fin du fichier   
On selectionne les 10 premières lignes   
On fait ctrl+K  
On place le curseur tout à la fin et on fait ctrl + u  


#### 4. Annulez cette action

Alt + u


#### 5. Enregistrez le fichier avant de quitter nano

```
ctrl + o  
ctrl + x
```

## Exercice 4


#### 1. Commencez par créer une copie de ce fichier, que vous appellerez .bashrc_bak

`cp . bashrc . bashrc_bak`
  

#### 2. Editez le fichier .bashrc avec nano et décommentez la ligne force_color_prompt=yes pour activer la couleur. Enregistrez le fichier et quittez nano.

`nano .bashrc`  
on a décommenté la bonne ligne et on a enregistré


#### 3. Le fichier .bashrc est lu au démarrage du shell ; pour le recharger, il faudrait donc se déconnecter puis se reconnecter ; mais il existe un autre moyen : la commande source .bashrc. Testez-la, l’invite de commande devrait immédiatement passer en couleurs.

l'invité de commande est passé en couleur 


#### 4. Les couleurs par défauts (surtout celle du dossier courant) ne sont pas très visibles. Dans .bashrc, cherchez les lignes commençant par PS1= ; elles indiquent la mise en forme de l’invite de commande (selon que l’on est en couleurs ou non.

```bash
PS1='${debian_chroot:+($debian_chroot)}\[\033[91m\][\A] - \[\033[01;92m\]\u@\h\[\033[00m\]:\[\033[01;96m\]\w\[\033[00m\]\$ '
```
pour afficher l'heure entre crochet on met [\A]   
92 c'est du vert clair   
96 c'est du cyan  
91 c'est du light rouge  